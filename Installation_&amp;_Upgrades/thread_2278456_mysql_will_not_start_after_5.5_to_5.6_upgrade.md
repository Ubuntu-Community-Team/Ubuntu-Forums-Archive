---
title: "mysql will not start after 5.5 to 5.6 upgrade"
date: 2015-05-16
forum: Installation &amp; Upgrades
---

### Post by kmand on 2015-05-16
I just did a double Ubuntu upgrade 14.04->14.10->15.04, which sent me from mysql server 5.5.43 to 5.6.24.

Now if I run "service mysql start" it hangs and the mysql log shows

150516 09:47:00 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql

/usr/sbin/mysqld: Can't read dir of '/etc/mysql/mysql.conf.d/' (Errcode: 13 - Permission denied)
Fatal error in defaults handling. Program aborted
150516 09:47:00 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

Yet as far as permission

# ls -ld /etc/mysql/mysql.conf.d
drwxr-xr-x 2 root root 4096 May 15 03:56 /etc/mysql/mysql.conf.d
# ls -l /etc/mysql/mysql.conf.d
total 8
-rw-r--r-- 1 root root 3027 Feb 17 14:51 mysqld.cnf
-rw-r--r-- 1 root root 21 Feb 11 10:10 mysqld_safe_syslog.cnf

---

### Post by kmand on 2015-05-29
I found the problem. Apparmor still had the old 5.5 configuration file, and the config directory for mysql had changed in 5.6

---

