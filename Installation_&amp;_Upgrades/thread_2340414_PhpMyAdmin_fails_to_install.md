---
title: "PhpMyAdmin fails to install"
date: 2016-10-18
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2016-10-18
```
# apt-get remove phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dbconfig-common libjs-sphinxdoc libjs-underscore libmcrypt4 php-gettext php-tcpdf php5-gd
  php5-mcrypt
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 23.6 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 275276 files and directories currently installed.)
Removing phpmyadmin (4:4.4.13.1-1) ...
dbconfig-common: dumping mysql database phpmyadmin to /var/tmp/phpmyadmin.phpmyadmin.2016-10-18-22.32.mysql.esJVjQ.
database does not exist.
dbconfig-common: dropping mysql database phpmyadmin.
dropping database phpmyadmin: database does not exist.
dbconfig-common: revoking privileges for user phpmyadmin on phpmyadmin.
revoking access to database phpmyadmin from phpmyadmin@localhost: success.
Conf phpmyadmin disabled.
apache2_invoke postrm: Disable configuration phpmyadmin
Processing triggers for man-db (2.7.4-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 removed doc-base file...
Registering documents with scrollkeeper...
root@ronald-desktop:/var/lib/mysql# apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,722 kB of archives.
After this operation, 23.6 MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) wily/universe phpmyadmin all 4:4.4.13.1-1 [3,722 kB]
Fetched 3,722 kB in 3s (1,239 kB/s)     
Preconfiguring packages ...
Selecting previously unselected package phpmyadmin.
(Reading database ... 273881 files and directories currently installed.)
Preparing to unpack .../phpmyadmin_4%3a4.4.13.1-1_all.deb ...
Unpacking phpmyadmin (4:4.4.13.1-1) ...
Processing triggers for doc-base (0.10.6) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up phpmyadmin (4:4.4.13.1-1) ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/dbconfig-common/phpmyadmin.conf with new version
Replacing config file /etc/phpmyadmin/config-db.php with new version
granting access to database phpmyadmin for phpmyadmin@localhost: success.
verifying access for phpmyadmin@localhost: success.
dbconfig-common: dumping mysql database phpmyadmin to /var/tmp/phpmyadmin.phpmyadmin.2016-10-18-22.35.mysql.2Yg4Mq.
database does not exist.
dbconfig-common: dropping old mysql database phpmyadmin.
dropping database phpmyadmin: database does not exist.
creating database phpmyadmin: success.
verifying database phpmyadmin exists: success.
populating database via sql...  error encountered populating database:
mysql said: ERROR 1050 (42S01) at line 30: Table '`phpmyadmin`.`pma__bookmark`' already exists
dbconfig-common: phpmyadmin configure: aborted.
dbconfig-common: flushing administrative password
done.
dbconfig-common: flushing administrative password
apache2_invoke: Enable configuration phpmyadmin
```



The installation screen shows at the end:

 ```
An error occurred while installing the database:                                               
    &#9474;                                                                                                
    &#9474; mysql said: ERROR 1050 (42S01) at line 30: Table '`phpmyadmin`.`pma__bookmark`' already        
    &#9474; exists . Your options are:                                                                     
    &#9474;  * abort - Causes the operation to fail; you will need to downgrade,                           
    &#9474;    reinstall, reconfigure this package, or otherwise manually intervene    

```


```
l# mysql -uroot -p
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 298
Server version: 10.0.25-MariaDB-0ubuntu0.15.10.1 (Ubuntu)

Copyright (c) 2000, 2016, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> 

```

```
# php --version
PHP 5.6.11-1ubuntu3.4 (cli) 
Copyright (c) 1997-2015 The PHP Group
Zend Engine v2.6.0, Copyright (c) 1998-2015 Zend Technologies
    with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2015, by Zend Technologies


```
What can I do to get phpmyadmin installed?

---

### Post by Zero_Bytes on 2016-10-19
Have you tried ```
 apt-get purge phpmyadmin 
``` and then install

---

### Post by ELMIT on 2016-10-19
Thanks that helped.

Although I lost my root password during that process, but I reset it (finally) to a much stronger one.

---

