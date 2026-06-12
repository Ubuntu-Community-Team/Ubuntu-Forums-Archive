---
title: "C programming with MySQL"
date: 2015-04-26
forum: Installation &amp; Upgrades
---

### Post by VicKos on 2015-04-26
Hello to the community :-)
I have made a program in C language that uses MySQL.
I have problems with the installation of MySQL in my system.
The program is ok regarding MySQL connection with C, as I have it running in my work's pc. I can't install though in my home's station, and I need it for educational purposes..
Any help would me much appreciated..

Some commands with their errors:

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.5 but it is not installed
E: Unmet dependencies. Try using -f.

~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.5
Suggested packages:
  tinyca mailx
The following NEW packages will be installed:
  mysql-server-5.5
0 upgraded, 1 newly installed, 0 to remove and 103 not upgraded.
6 not fully installed or removed.
Need to get 0 B/2093 kB of archives.
After this operation, 32,7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Setting up dpkg (1.17.5ubuntu5.4) ...
(Reading database ... 194600 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.5_5.5.43-0ubuntu0.14.04.1_amd64.deb ...
Aborting downgrade from (at least) 5.6 to 5.5.
If are sure you want to downgrade to 5.5, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.5_5.5.43-0ubuntu0.14.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.5_5.5.43-0ubuntu0.14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thank you for your time and your possible answers :-)
(System: Ubuntu 14.04 LTS 64-bit)

---

### Post by ubfan1 on 2015-04-26
Looks like a conflict between mysql-server-5.6 and 5.5.  The mysql-server package in Ubuntu 14.04  depends upon mysql-server-5.5, don't know why it's not the 5.6 version.  Do you really need version mysql server 5.5?  Do you already have the 5.6 version installed?  Check the packages which are installed by
> dpkg -l |grep mysql

---

### Post by VicKos on 2015-05-02
Thank you for your response! :-)

~$ dpkg -l |grep mysql
ii  libdbd-mysql-perl                                     4.025-1                                             amd64        Perl5 database interface to the MySQL database
ii  libmysqlclient18:amd64                                5.5.41-0ubuntu0.14.04.1                             amd64        MySQL database client library
iU  mysql-client-5.5                                      5.5.43-0ubuntu0.14.04.1                             amd64        MySQL database client binaries
iU  mysql-client-core-5.5                                 5.5.43-0ubuntu0.14.04.1                             amd64        MySQL database core client binaries
ii  mysql-common                                          5.5.43-0ubuntu0.14.04.1                             all          MySQL database common files, e.g. /etc/mysql/my.cnf
rc  mysql-common-5.6                                      5.6.19-0ubuntu0.14.04.1                             all          MySQL 5.6 specific common files, e.g. /etc/mysql/conf.d/my-5.6.cnf
iU  mysql-server                                          5.5.43-0ubuntu0.14.04.1                             all          MySQL database server (metapackage depending on the latest version)
ic  mysql-server-5.5                                      5.5.41-0ubuntu0.14.04.1                             amd64        MySQL database server binaries and system database setup
iU  mysql-server-core-5.5                                 5.5.43-0ubuntu0.14.04.1                             amd64        MySQL database server binaries

This is the result after  "dpkg -l |grep mysql"
Any thoughts?

---

### Post by ubfan1 on 2015-05-02
The command man dpkg-query has the meaning for the first two columns, and so it looks like the 5.6 common package was not "purged", since the config files still seem to be around.  Try the apt-get purge mysql-common-5.6  to see if that gets rid of all bits of the last 5.6 package.  The rest of the 5.5 package should then hopefully install.

---

### Post by VicKos on 2015-05-03
~$ sudo apt-get purge mysql-common-5.6 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

:/

I could try formatting my laptop and reinstall Ubuntu.. Even though I won't do anything differently than the last time, so it seems that the same problem would appear..

---

### Post by ubfan1 on 2015-05-03
Is the 5.6 package gone?  You could try purging all the mysql packages and just reinstall the mysql package (might need a client, not sure what will be installed from just mysql).

---

### Post by VicKos on 2015-05-06
I've formatted my laptop and I installed it (using sudo apt-get install libmysqlclient-dev)..
Thanks a lot for your answers though! :-)

---

