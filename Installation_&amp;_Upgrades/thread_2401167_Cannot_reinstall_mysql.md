---
title: "Cannot reinstall mysql"
date: 2018-09-14
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2018-09-14
I have been having problems with Owncloud after upgrading my server to 18.04 so I decided to try Nextcloud with Mariadb following these [instructions]("https://www.techrepublic.com/article/how-to-install-nextcloud-13-on-ubuntu-18-04/") The command "sudo systemctl start mariadb" kept timing out so I gave up and decided to try again with Owncloud and mysql. But then whenever I tried to use "sudo mysql -u root -p" I got the message
> ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) 
I discovered this was probably to do with Mariadb and so completely purged both mysql and Mariadb. Now when I try and re-install mysql I get the following message and after installation cannot log in to mysql
> Configuring mysql-server-5.7 Automatic maintenance of MySQL server daemon disabled
Packaging maintainer scripts detected a case that it does not know how to handle and cannot continue configuring MySQL. Automatic management of your MySQL installation has been disabled to allow other packaging tasks to complete. For more details, see /etc/mysql/FROZEN.
The contents of etc/mysql/FROZEN read:
> This MySQL or variant installation has entered "frozen mode". Maintainer scripts will avoid making changes or starting the daemon until manually released from this state. See /usr/share/doc/mysql-common/README for general information about this mode.

In this particular case, an incompatible downgrade attempt has been detected. This can be resolved in one of two ways:

Change the contents of /var/lib/mysql/ to contain database data that is compatible with the currently installed MySQL or variant daemon version. For example: you could restore from a backup. Alternatively you could do a dump using a future version binary and then a restore using the current version binary.

Switch to a MySQL or variant daemon version that is compatible with the data currently in /var/lib/mysql/. For example, if you have attempted a downgrade from mysql-server-5.7 to mysql-server-5.6, you could "apt install mysql-server-5.7" again.
I renamed the three files there that had to do with mysql and purged mysql again and tried another install, only to get the same message again. Any help to get mysql installed and working would be greatly appreciated.

---

### Post by LHammonds on 2018-09-14
Sounds like you need to remove MySQL and install MariaDB.  I know you can go from MySQL to MariaDB but not sure about going the other way.

Also, if this was a long-running database, you might need to run an upgrade command called "mysql_upgrade" to update the database version.

Before doing these changes, did you do a backup of the databases using mysqldump?

LHammonds

---

### Post by stepheny on 2018-09-14
Tried "mysql_upgrade" but it gives the warning 

> mysql_upgrade: Got error: 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) while connecting to the MySQL server
Upgrade process encountered error and will not continue.

I have prged *mysql* and *mariadb* and run autoremove and autoclean and tried to reinstall mysql-server but still kee getting this FROZEN message.

---

### Post by stepheny on 2018-09-14
Fixed it! The problem was the file /etc/mysql which wasn't being removed by purge. I renamed it with mv and then installed mysql-server and now I can log into mysql.

---

### Post by limax9s on 2018-09-15
[COLOR=#000000]The problem is that the package is still on the system in an half-installed and half-configured state and needs to be explicitly removed.
dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured [/COLOR][URL="https://discord.software/"][COLOR=#000000][FONT=Arial]Discord[/FONT]
[/COLOR][/URL][COLOR=#000000]
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.7 [/COLOR][URL="https://adobereader.onl/"][COLOR=#000000][FONT=Arial]Adobe Reader[/FONT]
[/COLOR][/URL][COLOR=#000000]
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
What its really saying is that the package mysql-server-5.7 is a dependency for mysql-server, is already installed, but is not configured. So you need to purge it to remove those breadcrumbs left behind by mysql-server-5.7.
sudo apt purge mysql-server mysql-server-5.7
Rationale
When you install software using apt, it automatically handles dependencies for you as well. [/COLOR][URL="https://itunes.red/"][COLOR=#000000][FONT=Arial]iTunes[/FONT]
[/COLOR][/URL][COLOR=#000000]
When you remove certain packages, it may not handle those same dependencies. In the case of this post, that dependency is mysql-server-5.7.
You can check to see a package state by issuing the following command.
dpkg-query -l [package-name-here]
Usually if you see the code un or rc to the left of the package name, you'll be able to tell if it actually is a broken package.
When I experienced this issue, it was with libapache2-mod-php and libapache2-mod-php7.0. This was my output.[/COLOR]

---

