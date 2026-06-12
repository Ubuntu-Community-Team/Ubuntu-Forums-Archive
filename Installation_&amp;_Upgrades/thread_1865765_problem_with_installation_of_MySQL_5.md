---
title: "problem with installation of MySQL 5"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by MarwaDim on 2011-10-20
Hi linux users,

I've a problem in installing my MySQL 5,
could someone help me please?

I used the terminal to do that : 
```

marwa@ubuntu:~$ sudo su
[sudo] password for marwa: 
root@ubuntu:/home/marwa# apt-get install mysql-server mysql-client

```I was asked to provide a password for the mysql root, just after that I had this:
```

Setting up mysql-cluster-client-5.1 (7.1.9a-0ubuntu2) ...
Setting up mysql-cluster-server-5.1 (7.1.9a-0ubuntu2) ...
 * Stopping MySQL database server mysqld                                [ OK ] 
chown: cannot access `/var/run/mysqld': No such file or directory
 * Starting MySQL database server mysqld                                 [ OK ] 
/etc/init.d/mysql: line 116: /etc/mysql/debian-start: No such file or directory
invoke-rc.d: initscript mysql, action "start" failed.

```could someone help me please :-(

---

