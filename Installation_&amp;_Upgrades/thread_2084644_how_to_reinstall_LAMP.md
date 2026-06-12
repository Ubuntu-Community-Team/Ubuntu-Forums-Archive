---
title: "how to reinstall LAMP"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by mahfud on 2012-11-16
i need your help,..
this is the first time for me in using ubuntu..
i get a problem when i try to install LAMP on ubuntu 11.10.:confused:
installation  not success.. and this is my fault, because i was delete every folder php5:(

when i try tutorial that's given by AM Dave 
[http://ubuntuforums.org/showthread.php?p=10472476](http://ubuntuforums.org/showthread.php?p=10472476)

the result :
```
root@jm-M2009:/home/jm# apt-get install --reinstall apache2 php5-mysql libapache2-mod-php5 mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 4 reinstalled, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/79.8 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 304975 files and directories currently installed.)
Preparing to replace apache2 2.2.20-1ubuntu1.3 (using .../apache2_2.2.20-1ubuntu1.3_i386.deb) ...
Unpacking replacement apache2 ...
Preparing to replace mysql-server 5.1.66-0ubuntu0.11.10.2 (using .../mysql-server_5.1.66-0ubuntu0.11.10.2_all.deb) ...
Unpacking replacement mysql-server ...
Preparing to replace php5-mysql 5.3.6-13ubuntu3.9 (using .../php5-mysql_5.3.6-13ubuntu3.9_i386.deb) ...
Unpacking replacement php5-mysql ...
Setting up libapache2-mod-php5 (5.3.6-13ubuntu3.9) ...
Error: The new file /usr/share/php5/php.ini-production does not exist!
dpkg: error processing libapache2-mod-php5 (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up apache2 (2.2.20-1ubuntu1.3) ...
Setting up mysql-server (5.1.66-0ubuntu0.11.10.2) ...
Setting up php5-mysql (5.3.6-13ubuntu3.9) ...
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jm-M2009:/home/jm#
```

could you help me to fix it??
thanks.

---

