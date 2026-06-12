---
title: "Upgrade to MySQL 5.0.22 under Ubuntu Dapper Drake kills previous version of MySQL"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by dracus on 2007-08-21
Greetings, all...

I have an Ubuntu server running Dapper Drake (6.04) that had a working install of MySQL on it. The update manager told me that updates were available, and without thinking, I clicked on install. Previously, it was a stock install of MySQL from the CD.  Afterwards, I could not get MySQL to run. When I run '/etc/init.d/mysql start', I get the following errors:

> Starting MySQL database server: mysqld.
> .
> .
> .
> .
> .
> .
> .
> .
> .
> .
> .
> .
> .
> ...failed or took more than 6s.
> Please take a look at the syslog.
> /usr/bin/mysqladmin: connect to server at 'localhost' failed
> error: 'Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)'
> Check that mysqld is running and that the socket: '/var/lib/mysql/mysql.sock' exists!

So I check /var/lib/mysql, and there is no socket file, when there was one before the upgrade. I can touch and read files as either root or mysql in that directory, so the permissions are ok. So I check /var/log/syslog, and find these errors:

> Aug 20 13:42:01 localhost mysqld_safe[22051]: started
> Aug 20 13:42:01 localhost mysqld[22054]: 070820 13:42:01 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'
> Aug 20 13:42:01 localhost mysqld[22054]: 070820 13:42:01 [ERROR] Aborting
> Aug 20 13:42:01 localhost mysqld[22054]:
> Aug 20 13:42:01 localhost mysqld_safe[22056]: ended
> Aug 20 13:42:16 localhost /etc/init.d/mysql[22191]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/my.cnf ping' resulted in
> Aug 20 13:42:16 localhost /etc/init.d/mysql[22191]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
> Aug 20 13:42:16 localhost /etc/init.d/mysql[22191]: error: 'Can't connect to local MySQL server through socket '/var/lib/mysql/mysql.sock' (2)'
> Aug 20 13:42:16 localhost /etc/init.d/mysql[22191]: Check that mysqld is running and that the socket: '/var/lib/mysql/mysql.sock' exists!
> Aug 20 13:42:16 localhost /etc/init.d/mysql[22191]:

So I 'ls -l /usr/share/mysql/english':

> total 28
> -rw-r--r-- 1 root root 25829 2007-03-21 17:06 errmsg.sys

'more'-ing this file gives me binary output. Should this be a binary file? Is this file not compatible between verisons of MySQL? Checking mysqld shows that it is version 5.0.22, but that the errmsg.sys file is older (the upgrade happened just a couple days ago). If that could be the problem, please let me know where I can grab a new version of that file. Thanks in advance.

---

### Post by JReagan1990 on 2007-08-21
My second suggestion is that you remove the MySQL package, and pop the install CD in and add it to your repositories.  *Server version of Ubuntu will require the command line *  You can then install the old version back by using the Synaptic(GUI), or Aptitude (CLI) - just navigate to the CD repository, and install the old version.


If this is a recurring problem, you might find it in the "Bugs" list in Launchpad.  There you might find people who have found solutions.


I hope this helps!

---

