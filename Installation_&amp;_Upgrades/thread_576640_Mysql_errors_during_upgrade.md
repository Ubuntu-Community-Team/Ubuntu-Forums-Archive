---
title: "Mysql errors during upgrade"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by Dan.Irving on 2007-10-15
Having trouble getting MySQL5 runing on my server.

Here is a list of what I have installed:

$ sudo dpkg -l|grep mysql
ii  libdbd-mysql-perl            3.0006-1                     A Perl5 database interface to the MySQL data
ii  libmysqlclient15off          5.0.24a-9ubuntu2.1           mysql database client library
ii  mysql-client-5.0             5.0.24a-9ubuntu2.1           mysql database client binaries
ii  mysql-common                 5.0.24a-9ubuntu2.1           mysql database common files (e.g. /etc/mysql
iF  mysql-server-5.0             5.0.24a-9ubuntu2.1           mysql database server binaries
ii  php5-mysql                   5.1.6-1ubuntu2.6             MySQL module for php5
ii  php5-mysqli                  5.1.6-1ubuntu2.6             MySQL Improved module for php5
$

Here is the error I get when I attempt an apt-get upgrade:

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld                                                                      [ ok ]
 * Starting MySQL database server mysqld                                                                      [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

Googling the Ubuntu forums for my errors I try dpkg --configure -a:
$ sudo dpkg --configure -a
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld                                                                      [ ok ]
 * Starting MySQL database server mysqld                                                                      [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
i$

AND I try apt-get -f install:
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld                                                                      [ ok ]
 * Starting MySQL database server mysqld                                                                      [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

My most recent errors in syslog:
Oct  2 19:10:06  mysqld_safe[31208]: PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
Oct  2 19:10:06  mysqld_safe[31208]: To do so, start the server, then issue the following commands:
Oct  2 19:10:06  mysqld_safe[31208]: /usr/bin/mysqladmin -u root password 'new-password'
Oct  2 19:10:06  mysqld_safe[31208]: /usr/bin/mysqladmin -u root -h  password 'new-password'
Oct  2 19:10:06  mysqld_safe[31208]: See the manual for more instructions.
Oct  2 19:10:06  mysqld_safe[31208]:
Oct  2 19:10:06  mysqld_safe[31208]: NOTE:  If you are upgrading from a MySQL <= 3.22.10 you should run
Oct  2 19:10:06  mysqld_safe[31208]: the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
Oct  2 19:10:06  mysqld_safe[31208]: able to use the new GRANT command!
Oct  2 19:10:06  mysqld_safe[31208]:
Oct  2 19:10:06  mysqld_safe[31208]: Please report any problems with the /usr/bin/mysqlbug script!
Oct  2 19:10:06  mysqld_safe[31208]:
Oct  2 19:10:06  mysqld_safe[31208]: The latest information about MySQL is available on the web at
Oct  2 19:10:06  mysqld_safe[31208]: [http://www.mysql.com](http://www.mysql.com)
Oct  2 19:10:06  mysqld_safe[31208]: Support MySQL by buying support/licenses at [http://shop.mysql.com](http://shop.mysql.com)
Oct  2 19:10:07  mysqld_safe[31412]: started
Oct  2 19:10:07  mysqld[31415]: 071002 19:10:07 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
Oct  2 19:10:07  mysqld[31415]: 071002 19:10:07 [ERROR] Do you already have another mysqld server running on port: 3306 ?
Oct  2 19:10:07  mysqld[31415]: 071002 19:10:07 [ERROR] Aborting
Oct  2 19:10:07  mysqld[31415]:
Oct  2 19:10:07  mysqld[31415]: 071002 19:10:07 [Note] /usr/sbin/mysqld: Shutdown complete
Oct  2 19:10:07  mysqld[31415]:
Oct  2 19:10:07  mysqld_safe[31417]: ended
Oct  2 19:10:22  /etc/init.d/mysql[31552]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Oct  2 19:10:22  /etc/init.d/mysql[31552]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Oct  2 19:10:22  /etc/init.d/mysql[31552]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Oct  2 19:10:22  /etc/init.d/mysql[31552]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Oct  2 19:10:22  /etc/init.d/mysql[31552]:

I've tried using apt-get remove, aptitude purge remove mysql-server-5.0, and even uncommenting and commenting out the old_password and skip-innodb lines  my.cnf.

By now I've probably borked MySQL beyond recognition.  This problem arose when the server hung during an apt-get upgrade attempt.  Any help? I'd rather not have to reimage if at all possible.

~~~~~~~~~~~~~~~~~~~~~~~~~~~

Attempted to full remove MySQL-server-5.0 from the system using sudo aptitude purge mysql-server-5.0 then tried to reinstall using aptitude instead of apt-get because it appeared as if apt-get thought the app was partially installed:

$ sudo aptitude install mysql-server-5.0
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  mysql-server-5.0
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.9MB of archives. After unpacking 67.4MB will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main mysql-server-5.0 5.0.24a-9ubuntu2.1 [24.9MB]
Fetched 24.9MB in 9m31s (43.6kB/s)
Preconfiguring packages ...
tar: ./config: time stamp 2007-10-09 16:02:22 is 586147.804105 s in the future
tar: ./templates: time stamp 2007-10-09 16:02:23 is 586148.803456 s in the future
tar: ./postinst: time stamp 2007-10-09 16:02:42 is 586167.803196 s in the future
tar: ./preinst: time stamp 2007-10-09 16:02:42 is 586167.802895 s in the future
tar: ./prerm: time stamp 2007-10-09 16:02:42 is 586167.802705 s in the future
tar: ./postrm: time stamp 2007-10-09 16:02:42 is 586167.802521 s in the future
tar: ./conffiles: time stamp 2007-10-09 16:02:42 is 586167.802329 s in the future
tar: ./md5sums: time stamp 2007-10-09 16:02:50 is 586175.79996 s in the future
tar: ./control: time stamp 2007-10-09 16:03:08 is 586193.799626 s in the future
tar: .: time stamp 2007-10-09 16:03:08 is 586193.799277 s in the future
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 17668 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.24a-9ubuntu2.1_i386.deb) ...
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld                                                                                                [ ok ]
 * Starting MySQL database server mysqld                                                                                                [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.24a-9ubuntu2.1) ...
 * Stopping MySQL database server mysqld                                                                                                [ ok ]
 * Starting MySQL database server mysqld                                                                                                [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
$

Nada

---

