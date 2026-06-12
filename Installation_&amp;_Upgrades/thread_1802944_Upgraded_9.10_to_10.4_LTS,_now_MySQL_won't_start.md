---
title: "Upgraded 9.10 to 10.4 LTS, now MySQL won't start"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by isthisyournacho on 2011-07-12
Hello all,

I have a development server that I have attempted the 9.10 -> 10.4 LTS upgrade on to see if there were any problems.  (Another catch is that I am running PHP 5.3 and 5.2 concurrently, and this has been successfully done.)

MySQl fails to start:
> root@dev11:/var/run/mysqld# /etc/init.d/mysql start
 * Starting MySQL database server mysqld
   ...fail!
Checking /var/log/syslog:
> Jul 12 16:07:01 dev11 /etc/init.d/mysql[14782]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jul 12 16:07:01 dev11 /etc/init.d/mysql[14782]: /usr/bin/mysqladmin: connect to server at 'localhost' failed
Jul 12 16:07:01 dev11 /etc/init.d/mysql[14782]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jul 12 16:07:01 dev11 /etc/init.d/mysql[14782]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jul 12 16:07:01 dev11 /etc/init.d/mysql[14782]: I've gone through numerous forums, checked permissions, etc.  the mysql.sock isn't there, and when I "touch" the file it does get created but doesn't seem to help at all.

Any ideas?

P.S. This server has had MySQL running for some time.  There are databases on there, but again they are used in development only.  I'd rather not uninstall/reinstall.

---

### Post by isthisyournacho on 2011-07-12
Ack, already solved.  Somehow mysql-server wasn't installed.  Now having a whole slew of problems.. but moving forward!

> apt-get install mysql-server

---

