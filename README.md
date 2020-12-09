[![Travis Build Status](https://travis-ci.org/smartapps-fr/bitbucket-pipelines-debian-8.svg?branch=master)](https://travis-ci.org/smartapps-fr/bitbucket-pipelines-debian-8)
[![Microbadger badge](https://images.microbadger.com/badges/image/smartapps/bitbucket-pipelines-php-mysql.svg)](https://microbadger.com/images/smartapps/bitbucket-pipelines-php-mysql)

# bitbucket-pipelines-debian-8

[Bitbucket Pipelines](https://bitbucket.org/product/features/pipelines) [Docker](https://www.docker.com/) image based on [Debian 8 _Jessie_](https://www.debian.org/releases/jessie/) with [PHP](http://php.net/)/[MySQL](https://www.mysql.com) (and more !)

More help in Bitbucket's [Confluence](https://confluence.atlassian.com/bitbucket/bitbucket-pipelines-beta-792496469.html)

Docker image at [swordfox/bitbucket-pipelines-debian-8:lastest](https://hub.docker.com/r/swordfox/bitbucket-pipelines-debian-8/)

## Packages installed

 - `php5-apcu`, `php5-cli`, `php5-curl`, `php5-gd`, `php5-geoip`, `php-gettext`, `php5-imagick`, `php5-intl`, `php5-json`, `php5-mcrypt`, `php5-memcached`, `php5-mysqlnd`, `php5-sqlite`, `php5-xdebug`, `php5-xhprof`, `php5-xmlrpc`, `memcached`, `imagemagick`, `openssh-client`, `curl`, `rsync`, `gettext`, `zip`, `bzip2`, `git`, `subversion`
 - [Perl](https://www.perl.org/) 5.20
 - [Python](https://www.python.org/) 2.7 & 3.4
 - [MySQL](https://www.mysql.com/) 5.5 (user `root:root`)
 - [PHP](http://www.php.net/) 5.6
 - [Ruby](https://www.ruby-lang.org/) 2.1
 - [Node.js](https://nodejs.org/) 10.x LTS (you can use [`n`](https://github.com/tj/n) to interactively manage your Node.js versions)
 - [PHPUnit](https://phpunit.de/) 5.7
 - Latest [Composer](https://getcomposer.org/), [Gulp](http://gulpjs.com/), [Webpack](https://webpack.github.io/), [Mocha](https://mochajs.org/), [Grunt](http://gruntjs.com/), [Codeception](https://codeception.com/), [Yarn](https://yarnpkg.com/), [n](https://github.com/tj/n)

## Sample `bitbucket-pipelines.yml`

```YAML
image: swordfox/bitbucket-pipelines-debian-8:lastest
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost --user=root --password=root -e "CREATE DATABASE test;"
          - composer config -g github-oauth.github.com XXXXXXXX
          - composer install --no-interaction --no-progress --prefer-dist
          - npm install --no-spin
          - gulp
```
