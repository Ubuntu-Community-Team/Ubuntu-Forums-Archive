---
title: "Cannot start mysql - &quot;Can't connect to local MySQL server through socket:&quot;"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by josh6847 on 2010-03-15
I am getting the following error when starting mysql using 'sudo /etc/init.d/mysql start':

Mar 15 16:33:56 MoodFishDev /etc/init.d/mysql[18317]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Mar 15 16:33:56 MoodFishDev /etc/init.d/mysql[18317]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Mar 15 16:33:56 MoodFishDev /etc/init.d/mysql[18317]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Mar 15 16:33:56 MoodFishDev /etc/init.d/mysql[18317]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Mar 15 16:33:56 MoodFishDev /etc/init.d/mysql[18317]:

I have tried manually creating the mysqld.sock file and I have checked permissions. Still no luck. This is a cloned ubuntu 8.04 slice from slicehost. I have done this before and never had problems with the mysql installation. Any ideas?

---

### Post by josh6847 on 2010-03-15
Had the wrong bind-address. Problem solved.

---

