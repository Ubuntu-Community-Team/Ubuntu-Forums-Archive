---
title: "unable to connect to mysql"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by proggrammer on 2013-03-15
Hi,

I am sorry for posting a popular question, but no available solution could help me.

mysql -uroot -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I did:
me@System / $ ps -e|grep mysqld 
 5354 pts/0    00:00:00 mysqld_safe
 5713 pts/0    00:00:07 mysqld

I even can see that phpmyadmin is working.
Kindly suggest me some solution.

---

### Post by matt_symes on 2013-03-15
Hi

Is the socket actually there ? Please post the output of...

```
ls -l /var/run/mysqld/mysqld.sock
```

It may be an idea to post the config file as well.

```
cat /etc/mysql/my.cnf
```

Kind regards

---

### Post by steeldriver on 2013-03-15
fyi that's exactly the error I get when the mysql server isn't running:
```

$ sudo service mysql stop
mysql stop/waiting
$
$ mysql -uroot -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

---

