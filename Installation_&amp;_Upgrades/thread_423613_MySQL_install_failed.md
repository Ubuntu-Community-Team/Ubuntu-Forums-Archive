---
title: "MySQL install failed"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by Alex N on 2007-04-26
I tried installing MYSQL without any luck. The error message appears  when I am trying to start
mysqld.

[Warning] Can't create test file /var/lib/mysql/desktop.lower-test
070426  9:49:40  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.

what's wrong ?

---

### Post by Alex N on 2007-04-27
Some additional information :

/var/run/mysqld    does not exist
/etc/mysql/my.cnf    does not exist - there is debian.cnf
all mysql directories are owned by user mysql group mysql.
the group exists, user does not.

complete deinstall of mysql is not possible - apt-get refuses to do it

---

