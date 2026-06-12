---
title: "mysql can't start"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by s0lid on 2005-08-23
i can't install mysql-server correctly. here's how i did it

# apt-get install mysql-server mysql-client mysql-doc



Preconfiguring packages ...
Selecting previously deselected package mysql-client.
(Reading database ... 78284 files and directories currently installed.)
Unpacking mysql-client (from .../mysql-client_4.0.23-3ubuntu2_i386.deb) ...
Selecting previously deselected package mysql-doc.
Unpacking mysql-doc (from .../mysql-doc_4.0.23-1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_4.0.23-3ubuntu2_i386.deb) ...
Setting up mysql-client (4.0.23-3ubuntu2) ...
Setting up mysql-doc (4.0.23-1) ...

Setting up mysql-server (4.0.23-3ubuntu2) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.

root@natalie:/home/s0lid # apt-get install mysql
root@natalie:/home/s0lid # /etc/init.d/mysql restart
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.


snip from /var/log/syslog:

Aug 23 13:08:19 natalie mysqld_safe[11857]: started
Aug 23 13:08:19 natalie mysqld[11861]: 050823 13:08:19 /usr/sbin/mysqld: Can't open file: 'user.MYI'. (errno: 142)
Aug 23 13:08:19 natalie mysqld[11861]: 050823 13:08:19 Fatal error: Can't open privilege tables: File '/usr/share/mysql/charsets/?.conf' not found (Errcode: 2)
Aug 23 13:08:19 natalie mysqld[11861]: 050823 13:08:19 Aborting
Aug 23 13:08:19 natalie mysqld[11861]:
Aug 23 13:08:19 natalie mysqld[11861]: 050823 13:08:19 /usr/sbin/mysqld: Shutdown Complete
Aug 23 13:08:19 natalie mysqld[11861]:
Aug 23 13:08:19 natalie mysqld_safe[11863]: ended
Aug 23 13:08:25 natalie /etc/init.d/mysql[11907]: 0 processes alive and '/usr/bin/mysqladmin --defaults-extra-file=/etc/mysql/debian.cnf ping' resulted in
Aug 23 13:08:25 natalie /etc/init.d/mysql[11907]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Aug 23 13:08:25 natalie /etc/init.d/mysql[11907]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Aug 23 13:08:25 natalie /etc/init.d/mysql[11907]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Aug 23 13:08:25 natalie /etc/init.d/mysql[11907]:

---

### Post by neomingus on 2005-08-24
```
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
```
This message usually means that networking option is disabled in my.cnf file. To fix this: go to /etc/mysql/my.cnf, comment out the configuration item of skip-networking, then restart your mysql server.
Good luck.

---

