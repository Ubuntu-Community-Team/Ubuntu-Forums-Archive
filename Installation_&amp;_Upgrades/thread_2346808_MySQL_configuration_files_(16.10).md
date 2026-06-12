---
title: "MySQL configuration files (16.10)"
date: 2016-12-18
forum: Installation &amp; Upgrades
---

### Post by qazwsxedc2016 on 2016-12-18
I just installed Ubuntu 16.10 and I'm confused by the number and similarity of configuration files provided by the package for MySQL:

/etc/mysql/conf.d/**mysql.cnf**
/etc/mysql/conf.d/**mysqldump.cnf**
/etc/mysql/mysql.conf.d/**mysqld.cnf**
/etc/mysql/mysql.conf.d/**mysqld_safe_syslog.cnf**
/etc/mysql/**debian.cnf**
/etc/mysql/**debian-start**
/etc/mysql/**my.cnf**
/etc/mysql/**my.cnf.fallback**
/etc/mysql/**mysql.cnf**

It honestly looks like the package maintainer was trying to mess with us mortal users. Can somebody please explain the hierarchy and precedence?

---

### Post by Keith_Helms on 2016-12-19
Here's the description of the mysql config files:
[http://dev.mysql.com/doc/refman/5.7/en/option-files.html](http://dev.mysql.com/doc/refman/5.7/en/option-files.html)

The debian named files appear to be used to rotate the mysql logfiles.  Look at /etc/logrotate.d/mysql-server

---

