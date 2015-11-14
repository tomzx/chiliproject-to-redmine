# Chiliproject to redmine

This is a simple guide for migrating from Chiliproject (v3.x) to Redmine (v3.x).

**Note:** This guide was tested on a Chiliproject v3.8.0 to Redmine 3.0.4 migration. There may be issues with lower versions of Chiliproject as it will attempt to rollback migrations that may not have been executed. This should be easily fixed by making the appropriate changes in the `chiliproject-to-redmine.sh` to remove the migrations that were not executed.

## Overview

* Copy configuration files
* Copy files (attachment)
* Backup your database
* Rollback Chiliproject migrations
* Run Redmine migrations

**Note:** This guide will not go through the steps of migrating plugins. We suggest you follow [Redmine's plugin wiki](https://www.redmine.org/projects/redmine/wiki/Plugins) if you have any question regarding plugins.

## Prerequisites

This will assume that the following in the instructions below (simply replace the values with yours and it will work the same):

* /var/www/redmine (Redmine installation)
* /var/www/chiliproject (Chiliproject installation)

## Step by step

1. Stop your Chiliproject instance.
2. Backup your Chiliproject database.
3. Configure `chiliproject-to-redmine.sh` with the appropriate environment to use. By default, it will be `production`.
4. Run `chiliproject-to-redmine.sh` in the `/var/www/chiliproject` directory. This will basically rollback every migration done by Chiliproject.
5. Run `bundle exec rake db:migrate` in the `/var/www/redmine` directory. This will update your Redmine to the latest migration state.
6. You may now start Redmine.
7. Done.

## License

The code is licensed under the [MIT license](http://choosealicense.com/licenses/mit/). See [LICENSE](LICENSE).