# Dokku Rollbar

Dokku Rollbar is a plugin for [Dokku](https://github.com/progrium/dokku) that notifies Rollbar of deployments.

This dokku plugin could be easily modified to support other error trackers (Sentry, etc).

## Installation

Verified to work on dokku 0.5+, will probably work without modification on early dokku versions.
```sh
$ dokku plugin:install https://github.com/iloveitaly/dokku-rollbar.git
```

The plugin pulls the Rollbar access token from your app's `ROLLBAR_TOKEN` and
your environment from `ROLLBAR_ENV`, `RAILS_ENV` or `RACK_ENV`. The app environment
will default to `production` if none of them is not set.

## Dependencies

There is an issue with the way old versions extract the git commit hash
(see [#4](https://github.com/iloveitaly/dokku-rollbar/issues/4))

For now we use the `GIT_REV` variable set by [dokku-git-rev](https://github.com/dokku-community/dokku-git-rev)
which is supposed to be part of dokku core in future versions.
`dokku-rollbar` will work without the plugin installed, but will report an incorrect
commit hash.

```sh
$ dokku plugin:install https://github.com/dokku-community/dokku-git-rev.git --name dokku-git-rev
```

## Commands

No commands. If `ROLLBAR_TOKEN` is set, Rollbar will be notified of each deploy.

## Inspiration

* https://github.com/Flink/dokku-airbrake-deploy
* https://github.com/ribot/dokku-slack
* https://github.com/nickstenning/dokku-webhooks

## [License](LICENSE)
