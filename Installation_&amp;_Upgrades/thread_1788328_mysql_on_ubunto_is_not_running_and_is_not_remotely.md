---
title: "mysql on ubunto is not running and is not remotely accessible"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by qasibeat on 2011-06-22
Currently i installed ubunot on ubunto 4.4, and using following commands i can see mysql, mysqld running

```
 ps -ef | grep mysql
 ps -ef | grep mysqld
```
but when I run, netstat i don't see mysql and 3306 anywhere. in my.cnf file, i have given my ip and port is 3306.

also when i run this command

```
sudo netstat -tap | grep mysql
```
i don't see anything and commands

I needed to run the mysql 5 on port 3306 and on ip=x.x.x.x for remotely accessible


I was looking into it and found following error.log

110622 11:37:37 [Note] Plugin 'FEDERATED' is disabled.
110622 11:37:37  InnoDB: Started; log sequence number 0 44233
110622 11:37:37 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address
110622 11:37:37 [ERROR] Do you already have another mysqld server running on port: 3306 ?
110622 11:37:37 [ERROR] Aborting


Looking forward to your reply

---

