---
title: "MySQL ERROR 2002 (HY000)"
date: 2016-09-27
forum: Installation &amp; Upgrades
---

### Post by reza.mrtz on 2016-09-27
Hello
I have a problem with Myql. Because of some troubles I removed Mysql and reinstall it with "brew" command. Now when I try to connect to Mysql, I get this error:
```
ERROR 2002 (HY000): Can't connect to local Mysql server through socket '/var/run/mysqld/mysqld.sock' (2) .
``` 
In this directory: "/var/run/" there is no Mysql folder. But in terminal when I type  "mysql --version", this is the output:
```
mysql  Ver 14.14 Distrib 5.7.15, for Linux (x86_64) using  EditLine wrapper
```
Because of some errors about packages and dependencies, I cannot remove and reinstall mysql at all and also can not connect to Mysql cuz of this:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) 
```
 any one knows how should I fix this? :(

---

### Post by SeijiSensei on 2016-09-27
Can you connect using "mysql -h localhost ..."?  That talks to the server over the "lo" network interface rather than through the socket interface.

---

### Post by reza.mrtz on 2016-09-28
no :( this damn error is still here
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

---

### Post by SeijiSensei on 2016-09-28
> Because of some troubles I removed Mysql and reinstall it with "brew" command. 

Why didn't you just use apt-get?  That works flawlessly for me.

---

