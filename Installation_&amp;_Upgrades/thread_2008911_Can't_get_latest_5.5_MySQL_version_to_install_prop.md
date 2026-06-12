---
title: "Can't get latest 5.5 MySQL version to install properly."
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by ubix on 2012-06-23
Hi,

Since Ubuntu's repositories for my Ubuntu 11.04 only contain older 5.1 MySQL release, which does not support all features I need, I tried to install the latest ***5.5.25 MySQL server*** directly from [www.mysql.com](www.mysql.com). I first removed the current 5.1 MySQL release, and then installed the downloaded ***5.5.25** version*. However, though it opened in  *Ununtu Software Centre* and installed fine, the server was not started. The latest new release is not installed in ***/usr/bin*** but rather in ***/opt/mysql/server-5.5/bin***

With the exception of *** mysqlaccess.conf, mysql_config, mysqld-debug, mysql_embedded, mysql_plugin***, which are missing in Ubuntu's 5.1 version, both distributions contain the same files, in their respective bin directories. 

I was hoping that by stopping the MySQL server and then copying 5.5.25 files over from ***/opt/mysql/server-5.5/bin*** to  ***/usr/bin***, while I kept 5.1 still installed, would not be a problem. 

Here is what I did:

```

1) su
2) service mysql stop
3) cp /opt/mysql/server-5.5/bin/* /usr/bin
4) mv /usr/bin/mysqld /usr/sbin
5) service mysql start

```
However, the server 5.5 again does not start, and I had to revert back to the lacking 5.1 version. Does anybody know, how to overcome this MySQL release upgrade problem? Are the maintainers of this package aware that we can not use MySQL 5.5.x on Ubuntu?

---

