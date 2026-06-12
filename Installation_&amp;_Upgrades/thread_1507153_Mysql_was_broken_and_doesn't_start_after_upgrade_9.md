---
title: "Mysql was broken and doesn't start after upgrade 9.10-&gt;10.04"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by surfer63 on 2010-06-11
I did a server upgrade using the familiar "sudo do-release-upgrade" but I had to Ctrl-C the mysql-server upgrade as it hung. The rest of the upgrade went fine.

So I got in my /var/log/dist-upgrade/20100611-0919/apt.log the following entries (after cat /var/log/dist-upgrade/20100611-0919/apt.log | grep mysql):
```
Installing libmysqlclient16 as dep of librdf0
Installing mysql-common as dep of libmysqlclient16
Installing mysql-client-5.0 as dep of mysql-server-5.0
Installing libmysqlclient15off as dep of mysql-client-5.0
Installing mysql-server-core-5.0 as dep of mysql-server-5.0
Installing mysql-server-core-5.1 as dep of akonadi-server
Installing mysql-server-5.1 as dep of mysql-server
Installing mysql-client-5.1 as dep of mysql-server-5.1
Investigating mysql-server-core-5.1
Package mysql-server-core-5.1 has broken dep on mysql-server-core-5.0
  Considering mysql-server-core-5.0 1 as a solution to mysql-server-core-5.1 2
  Added mysql-server-core-5.0 to the remove list
  Considering mysql-server-core-5.0 1 as a solution to mysql-server-core-5.1 2
  Fixing mysql-server-core-5.1 via remove of mysql-server-core-5.0
Investigating mysql-server-5.1
Package mysql-server-5.1 has broken dep on mysql-server-5.0
  Considering mysql-server-5.0 0 as a solution to mysql-server-5.1 1
  Added mysql-server-5.0 to the remove list
  Considering mysql-server-5.0 0 as a solution to mysql-server-5.1 1
  Fixing mysql-server-5.1 via remove of mysql-server-5.0
Investigating mysql-client-5.1
Package mysql-client-5.1 has broken dep on mysql-client-5.0
  Considering mysql-client-5.0 1 as a solution to mysql-client-5.1 0
  Holding Back mysql-client-5.1 rather than change mysql-client-5.0
Investigating mysql-server-5.1
Package mysql-server-5.1 has broken dep on mysql-client-5.1
  Considering mysql-client-5.1 0 as a solution to mysql-server-5.1 1
  Holding Back mysql-server-5.1 rather than change mysql-client-5.1
Investigating mysql-server
Package mysql-server has broken dep on mysql-server-5.1
  Considering mysql-server-5.1 1 as a solution to mysql-server 1
  Removing mysql-server rather than change mysql-server-5.1
Package zoneminder has broken dep on mysql-server
  Considering mysql-server 1 as a solution to zoneminder 0
  Removing zoneminder rather than change mysql-server
Installing mysql-server-5.1 as dep of mysql-server
Installing mysql-client-5.1 as dep of mysql-server-5.1
```
My main.log mentions (again grepped):```
2010-06-11 10:48:08,954 ERROR got an error from dpkg for pkg: 'mysql-server-5.1': 'subprocess installed post-installation script killed by signal (Interrupt)
2010-06-11 10:48:08,955 DEBUG running apport_pkgfailure() mysql-server-5.1: subprocess installed post-installation script killed by signal (Interrupt)
2010-06-11 10:48:09,422 ERROR got an error from dpkg for pkg: 'mysql-server': 'dependency problems - leaving unconfigured
2010-06-11 10:48:09,422 DEBUG running apport_pkgfailure() mysql-server: dependency problems - leaving unconfigured

```
However, my /etc/mysql/my.cnf is fully configured and still the same as before the upgrade.

After reboot I tried to do an "sudo apt-get update; sudo apt-get upgrade", but it didn't mention mysql. I used the (for me new) "sudo service mysql start" but it hung again.
when trying to "mysql ...." I got ```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
```
and indeed (off course) mysql is not running.
I tried "sudo apt-get remove mysql-server;sudo apt-get install mysql-server"  which worked fine but I still can't start mysql.
I also did a "sudo apt-get install mysql-client" and it installed the 5.1.41-3ubuntu12.3 client to no avail.

Anyone being able to shed some light on my problem?

Edit: I also used Synaptics function to "fix broken packages", which it did, but again without the desired result of having a starting and running mysql.

---

### Post by surfer63 on 2010-06-11
After a few hours troubleshooting I still can't get it to work. The only work-around is just issueing the command:```
sudo /usr/bin/mysqld_safe &
```
Then everything works as it should.

---

### Post by surfer63 on 2010-06-12
Somehow I completely missed the scripts in "/etc/init" that are being used by the "/lib/init/upstart-job".

Within the mysql.conf file you can find the line:
```
exec /usr/sbin/mysqld

```

I changed that to:
```
#exec /usr/sbin/mysqld
exec /usr/bin/mysqld_safe

```
as the first line (exec /usr/sbin/mysqld) only tries to stop mysql even if it's not running. That will never make mysql run on startup :p

---

