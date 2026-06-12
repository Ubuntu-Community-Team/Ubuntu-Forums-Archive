---
title: "Mysql Doesn't Work After Move From Fedora to Ubuntu!"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by dealmaker on 2007-03-16
Hi,
  I just moved from Fedora core 6 to Ubuntu 6.1.0.  I reinstalled LAMP in ubuntu, and I moved files in /var/lib/mysql in fedora to ubuntu.  But mysql fails to start afterward when I type "/etc/init.d/mysql start".  How do I fix it?  

Apache2 and php5 seems to work fine because I loaded a php file, and it loaded fine.
Thanks.

---

### Post by geirha on 2007-03-16
Does it give you any error messages when you try to start it?

Does **grep mysql /var/log/daemon.log** show any error messages?

---

### Post by dealmaker on 2007-03-16
Mar 16 08:51:56 laptop mysqld_safe[21473]: started
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56  InnoDB: Started; log sequence number 0 241355
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56 [Note] Recovering after a crash using /var/log/mysql/mysql-bin
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56 [Note] Starting crash recovery...
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56 [Note] Crash recovery finished.
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/host.frm' (errno: 13)
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56 [ERROR] /usr/sbin/mysqld: Can't find file: './mysql/host.frm' (errno: 13)
Mar 16 08:51:56 laptop mysqld[21476]: 070316  8:51:56 [ERROR] Fatal error: Can't open and lock privilege tables: Can't find file: './mysql/host.frm' (errno: 13)
Mar 16 08:51:56 laptop mysqld_safe[21487]: ended
Mar 16 08:52:11 laptop /etc/init.d/mysql[21628]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Mar 16 08:52:11 laptop /etc/init.d/mysql[21628]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Mar 16 08:52:11 laptop /etc/init.d/mysql[21628]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Mar 16 08:52:11 laptop /etc/init.d/mysql[21628]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Mar 16 08:52:11 laptop /etc/init.d/mysql[21628]: 

> **geirha said:**
> Does it give you any error messages when you try to start it?

Does **grep mysql /var/log/daemon.log** show any error messages?

---

### Post by geirha on 2007-03-16
It seems the mysql-server can't find /var/lib/mysql/mysql/host.frm, or lack permission to it. What does **ls -l /var/lib/mysql/mysql** say?

---

