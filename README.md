HackThis
========
[![project status](http://stillmaintained.com/HackThis/hackthis.co.uk.png)](http://stillmaintained.com/HackThis/hackthis.co.uk)

This repository contains all code for http://www.hackthis.co.uk. 

## Short instructions
* Import schema.sql into MySQL database, optionally import data files
* Edit include_path in `html/.htaccess`
* Copy `files/example.config.php` to `files/config.php` and edit details
* Create a min folder in both `html/css` and `html/js` and set their access to 777
* Create a users folder in `files/uploads` and set it's access to 777
* Check persmissions are set to 777 on both `files/cache` and `files/log`

## Longer instructions (Ubuntu)
Install Apache, PHP, MySQL and required libraries
````
sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5 mysql-server php5-mysql
````

Configure Apache
````
sudo nano /etc/apache2/sites-available/default
```

Example configuration
````
NameVirtualHost *

ServerAdmin admin@site.com

DocumentRoot /home/username/hackthis.co.uk/html

Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
````

Restart Apache
````
sudo /etc/init.d/apache2 restart
````

Import schema and testdata into MySQL
````
cd hackthis.co.uk
mysql -u <username> -p<password> < schema.sql
mysql -u <username> -p<password> < testdata.sql
````

Configure paths in .htaccess. Change include_path to the path of your hackthis.co.uk/files/ directory, with trailing slash
````
nano html/.htaccess
````

Create and configure config file. Change path to the path of your hackthis.co.uk directory, without trailing slash. Next set MySQL credentials to match those used in setup, database is `hackthis`. Facebook, twitter and lastfm API keys are not required but some features will not work correctly.
````
cp files/example.config.php files/config.php
nano files/config.php
````

Create and set new folder privilages
````
mkdir html/files/css/min
chmod 777 html/files/css/min
mkdir html/files/js/min
chmod 777 html/files/js/min
mkdir files/uploads/users
chmod 777 files/uploads/users
chmod 777 files/cache
chmod 777 files/logs
````

Navigate to website
````
http://localhost/?generate
````
`?generate` is required on any new page or after css/js changes to updated cache


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/HackThis/hackthis.co.uk/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

