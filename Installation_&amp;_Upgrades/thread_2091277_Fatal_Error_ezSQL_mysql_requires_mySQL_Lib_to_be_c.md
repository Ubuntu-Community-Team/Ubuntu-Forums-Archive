---
title: "Fatal Error: ezSQL_mysql requires mySQL Lib to be compiled and or linked in to the PH"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by mfriendly on 2012-12-04
Env: Ubuntu 12.04 precise;
PHP 5.3.10-1ubuntu3.4 with Suhosin-Patch (cli) (built: Sep 12 2012 18:59:41)

After an upgrade to Ubuntu precise and some development work on my test server I am now getting this error,  **Fatal Error:** ezSQL_mysql requires mySQL Lib to be compiled and or linked in to the PHP engine on the page
[http://euclid.psych.yorku.ca/datavis/milestones/](http://euclid.psych.yorku.ca/datavis/milestones/)

I checked phpinfo() via
[http://euclid.psych.yorku.ca/datavis/info.php](http://euclid.psych.yorku.ca/datavis/info.php)
and there was no mention of mysql support, so I ran, as sudo

# aptitude install php5-mysql
The following NEW packages will be installed:
  php5-mysql 
0 packages upgraded, 1 newly installed, 0 to remove and 129 not upgraded.
Need to get 77.1 kB of archives. After unpacking 272 kB will be used.
Get: 1 [http://debian.yorku.ca/ubuntu/](http://debian.yorku.ca/ubuntu/) precise-updates/main php5-mysql amd64 5.3.10-1ubuntu3.4 [77.1 kB]
Fetched 77.1 kB in 0s (607 kB/s)    
Selecting previously unselected package php5-mysql.
(Reading database ... 498345 files and directories currently installed.)
Unpacking php5-mysql (from .../php5-mysql_5.3.10-1ubuntu3.4_amd64.deb) ...
Processing triggers for libapache2-mod-php5 ...
 * Reloading web server config apache2                                                                                  [ OK ] 
Setting up php5-mysql (5.3.10-1ubuntu3.4) ...
                                         
However, I still get the same error, and phpinfo() still doesn't show mysql support.
On the other hand, from the command line, it seems to be there:
# php --ri mysql

mysql

MySQL Support => enabled
Active Persistent Links => 0
Active Links => 0
Client API version => 5.5.28
MYSQL_MODULE_TYPE => external
MYSQL_SOCKET => /var/run/mysqld/mysqld.sock
MYSQL_INCLUDE => -I/usr/include/mysql
MYSQL_LIBS => -L/usr/lib/x86_64-linux-gnu -lmysqlclient_r 

Directive => Local Value => Master Value
mysql.allow_persistent => On => On
mysql.max_persistent => Unlimited => Unlimited
mysql.max_links => Unlimited => Unlimited
mysql.default_host => no value => no value
mysql.default_user => no value => no value
mysql.default_password => no value => no value
mysql.default_port => no value => no value
mysql.default_socket => /var/run/mysqld/mysqld.sock => /var/run/mysqld/mysqld.sock
mysql.connect_timeout => 60 => 60
mysql.trace_mode => Off => Off
mysql.allow_local_infile => On => On

What else do I need to do to fix this?

---

