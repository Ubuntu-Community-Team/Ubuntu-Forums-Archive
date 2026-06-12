---
title: "mysql-server-5.7 failing to install (was marked as sercurty fix)"
date: 2016-06-27
forum: Installation &amp; Upgrades
---

### Post by egandt on 2016-06-27
I wwnt to install updates, one of which was mysql, now the package is installed, but apt says it is not as it will not complete the instllation:

```
oot@fileserver:/var/run# apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version (5.7.12-0ubuntu1.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mysql-server-5.7 (5.7.12-0ubuntu1.1) ...
[B]Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.[/B]
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
**  Package mysql-server-5.7 is not configured yet.**

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.7
 mysql-server


```
The cause of teh failure is simply the mysqld directory in /var/run is deleted as such it can not create any required files there to startup, why I do not know, but if I manually recreated the directory /var/run/mysqld owned by mysql:mysql then it starts up.

This is the directory pointed to by: /etc/mysql/mysql.conf.d/mysqld.cnf

Now I can change it in /etc/mysql/mysql.conf.d/mysqld.cnf to say /mysql/mysqld and mysqld will still run, but if I run "apt-get install mysql-server" I still get:

```
root@fileserver:/var/run# apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version (5.7.12-0ubuntu1.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up mysql-server-5.7 (5.7.12-0ubuntu1.1) ...
[B]Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.[/B]
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and it removed /var/run/mysqld and hence failed to start. 


Why did it remove /var/run/mysqld I do not have any pointers to the location anywhere in /etc/mysql first off any more, and mysql.cnf is set to use /mysq/mysqld for the moment as a test.  This makes no sense at all, it as if teh package is not using the /etc/mysql/mysql.conf.d/mysqld.cnf, but some other file.

Second to this affect I have my DBs installed in /websites/mysql and not the default location, but the package seems to want to load the DBs from the default as per syslog messages:

```
Jun 27 17:23:50 fileserver systemd[1]: Stopped MySQL Community Server.
Jun 27 17:23:50 fileserver systemd[1]: Starting MySQL Community Server...
Jun 27 17:23:50 fileserver mysql-systemd-start[28836]: MySQL system database not found. Please run mysql_install_db tool.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Control process exited, code=exited status=1
Jun 27 17:23:50 fileserver systemd[1]: Failed to start MySQL Community Server.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Unit entered failed state.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Failed with result 'exit-code'.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Jun 27 17:23:50 fileserver systemd[1]: Stopped MySQL Community Server.
Jun 27 17:23:50 fileserver systemd[1]: Starting MySQL Community Server...
Jun 27 17:23:50 fileserver mysql-systemd-start[28856]: MySQL system database not found. Please run mysql_install_db tool.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Control process exited, code=exited status=1
Jun 27 17:23:50 fileserver systemd[1]: Failed to start MySQL Community Server.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Unit entered failed state.
Jun 27 17:23:50 fileserver systemd[1]: mysql.service: Failed with result 'exit-code'.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Jun 27 17:23:51 fileserver systemd[1]: Stopped MySQL Community Server.
Jun 27 17:23:51 fileserver systemd[1]: Starting MySQL Community Server...
Jun 27 17:23:51 fileserver mysql-systemd-start[28874]: MySQL system database not found. Please run mysql_install_db tool.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Control process exited, code=exited status=1
Jun 27 17:23:51 fileserver systemd[1]: Failed to start MySQL Community Server.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Unit entered failed state.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Failed with result 'exit-code'.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Jun 27 17:23:51 fileserver systemd[1]: Stopped MySQL Community Server.
Jun 27 17:23:51 fileserver systemd[1]: Starting MySQL Community Server...
Jun 27 17:23:51 fileserver mysql-systemd-start[28880]: MySQL system database not found. Please run mysql_install_db tool.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Control process exited, code=exited status=1
Jun 27 17:23:51 fileserver systemd[1]: Failed to start MySQL Community Server.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Unit entered failed state.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Failed with result 'exit-code'.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Jun 27 17:23:51 fileserver systemd[1]: Stopped MySQL Community Server.
Jun 27 17:23:51 fileserver systemd[1]: mysql.service: Start request repeated too quickly.
Jun 27 17:23:51 fileserver systemd[1]: Failed to start MySQL Community Server.
Jun 27 17:25:01 fileserver CRON[28924]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)


That would be /var/lib/mysql


I have installed the following mysql packages:
ii  akonadi-backend-mysql                                       4:15.12.3-0ubuntu6                                  all          MySQL storage backend for Akonadi
ii  dbconfig-mysql                                              2.0.4ubuntu1                                        all          dbconfig-common MySQL/MariaDB support
ii  libdbd-mysql-perl                                           4.033-1build2                                       amd64        Perl5 database interface to the MySQL database
ii  libmysqlclient20:amd64                                      5.7.12-0ubuntu1.1                                   amd64        MySQL database client library
ii  libqt4-sql-mysql:amd64                                      4:4.8.7+dfsg-5ubuntu2                               amd64        Qt 4 MySQL database driver
ii  libqt5sql5-mysql:amd64                                      5.5.1+dfsg-16ubuntu7.1                              amd64        Qt 5 MySQL database driver
ii  mysql-client                                                5.7.12-0ubuntu1.1                                   all          MySQL database client (metapackage depending on the latest version)
ii  mysql-client-5.7                                            5.7.12-0ubuntu1.1                                   amd64        MySQL database client binaries
ii  mysql-client-core-5.7                                       5.7.12-0ubuntu1.1                                   amd64        MySQL database core client binaries
ii  mysql-common                                                5.7.12-0ubuntu1.1                                   all          MySQL database common files, e.g. /etc/mysql/my.cnf
iU  mysql-server                                                5.7.12-0ubuntu1.1                                   all          MySQL database server (metapackage depending on the latest version)
iF  mysql-server-5.7                                            5.7.12-0ubuntu1.1                                   amd64        MySQL database server binaries and system database setup
ii  mysql-server-core-5.7                                       5.7.12-0ubuntu1.1                                   amd64        MySQL database server binaries
ii  mysqltuner                                                  1.6.0-1                                             all          high-performance MySQL tuning script
ii  php-mysql                                                   1:7.0+35ubuntu6                                     all          MySQL module for PHP [default]
ii  php7.0-mysql                                                7.0.4-7ubuntu2.1                                    amd64        MySQL module for PHP
```


What is wrong and how do I fix it safely?
ERIC

---

### Post by egandt on 2016-06-27
Never mind I got the package to install, I needed to do do 2 things:

First /var/lib/mysql needs to be populated, with the following:
```
-rw-r-----   1 mysql mysql         56 Jun 15 16:40 auto.cnf
-rw-r--r--   1 mysql mysql          0 Jun 27 17:43 debian-5.7.flag
-rw-r-----   1 mysql mysql       1911 Jun 27 17:23 ib_buffer_pool
-rw-r-----   1 mysql mysql 1153433600 Jun 27 17:23 ibdata1
-rw-r-----   1 mysql mysql   67108864 Jun 27 17:23 ib_logfile0
-rw-r-----   1 mysql mysql   67108864 Jun 27 17:22 ib_logfile1
drwxr-x---   2 mysql mysql       4096 Jun 16 14:24 mysql
-rw-r--r--   1 mysql mysql          6 Jun 16 14:24 mysql_upgrade_info
drwxr-x---   2 mysql mysql       4096 Jun 16 14:24 performance_schema
drwxr-x---   2 mysql mysql      12288 Jun 15 16:40 sys
```


Note these are needed (in fact I used those from my initial install backup, so teh contents does not seem to matter only that they exist) for the install to complete, but are not used as the mysql.cnf points to in my case /websites/mysql for data files.

Second in the /etc/init.d/mysql file I had to added the following at right above:
sanity_checks() {

```
# ensure /var/run.mysqld exists and is owned my mysql
if [ ! -d /var/run/mysqld ]; then
        /bin/mkdir /var/run/mysqld
        /bin/chown mysql:mysql /var/run/mysqld
fi
```

This recreates the /var/run/mysqld directory that the package installation removes, and which causes mysqld to fail to start as a result.


Both issues seem to me to be related to poor packaging since the installer should look at mysql.cnf for the location of the data files (and not simply assume they were not moved as /var/lib is not a good location) and it should not remove and then not recreate /var/run/mysqld directory (which it does).

I hope that this helps someone else who has similar issues with updated mysql-server packages.

ERIC

---

