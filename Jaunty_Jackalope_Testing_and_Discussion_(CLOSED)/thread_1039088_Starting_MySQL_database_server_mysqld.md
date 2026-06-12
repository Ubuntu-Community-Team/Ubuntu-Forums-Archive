---
title: "Starting MySQL database server mysqld"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-01-14
System is calling for 'Restart' after 92 updates, but I am reluctant as this error occurred:

[B]Setting up mysql-server-5.1 (5.1.30-2ubuntu2) ...
 * Stopping MySQL database server mysqld                                                                  [ OK ] 
 * Starting MySQL database server mysqld                                                                  [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
dougie@DougiesLeanMachine:~$ 
[/B]
 Maybe a 'Restart' may solve?

---

### Post by Gourgi on 2009-01-14
i'm also getting this error
if you find a solution or bug report please post here

---

### Post by dinxter on 2009-01-14
mysql 5.1 fails to start since /var/run/mysqld/mysqld.sock doesnt exist. sadly creating it doesnt help as its removed during mysql startup. i'd recommend filing a bug, restarts wont help. possible a tempfs /var/run compared to debian problem? will look into it later if no-one posts a workaround

Jan 14 12:38:50 crystaltree /etc/init.d/mysql[12424]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jan 14 12:38:50 crystaltree /etc/init.d/mysql[12424]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jan 14 12:38:50 crystaltree /etc/init.d/mysql[12424]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jan 14 12:38:50 crystaltree /etc/init.d/mysql[12424]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jan 14 12:38:50 crystaltree /etc/init.d/mysql[12424]:

---

### Post by dinxter on 2009-01-14
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/316974](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/316974)

---

### Post by dinxter on 2009-01-14
seems to be 2 problematic bugs
1. the skip-bdb option in etc/mysql/my.cnf needs to be commented out
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/316849](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/316849)

2.  Table 'mysql.plugin' doesn't exist and Table 'mysql.host' doesn't exist  but cant run mysql_upgrade since we can t start mysql. fixed if you can remove all the old tables but needs a fix for preserving tables from 5.0

[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/316974](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.1/+bug/316974)

---

