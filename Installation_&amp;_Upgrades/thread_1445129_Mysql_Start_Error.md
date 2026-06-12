---
title: "Mysql Start Error"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by kannanjagadeesan on 2010-04-02
Hi Experts,

When I type mysql,
vignesh@vignesh:~$ mysql

I get this error.

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

So, I checked whether the file mysqld.sock is there in its respective folder, but I could not find that file.

Kindly tell me how to create the file and start mysql server.

Thanks & Regards,
Kannan

---

### Post by theDaveTheRave on 2010-04-02
kannanjagadeesan,

you can't 'create' the mysql.sock file per se, it is created by the mysql daemon when the process starts. I am assuming that you have correctly installed mysql and that it starts up at boot.

to check that the process is running

```

ps aux | grep mysql

```
will kick out a report similar to this if it is
```

root      2928  0.0  0.0   1872   468 ?        S    13:19   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     2970  0.0  2.8 130720 14112 ?        Sl   13:19   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3307 --socket=/var/run/mysqld/mysqld.sock

```

if it doesn't you will need to start the server, you would most likely want the server to run in the background and in safe mode (ie. if or some reason the server crashes it will automatically re-start for you), to start a non running mysql

```

mysqld_safe &

```
the & puts the process into the background.

If this is the first time you are running mysql there are a few 'security' things that you need to bear in mind, such as setting a 'non privileged user' for most general duties etc.

So now all you need to do is log in a the root user, and add ion a general user etc etc...



David

---

