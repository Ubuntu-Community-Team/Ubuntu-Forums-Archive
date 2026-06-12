---
title: "myphpadmin first time login gives access denied to www-data"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by j3cakes on 2007-10-02
I just installed phpmyadmin and when I try to login in (as root) I get the following message: 

Error #1045 - Access denied for user 'www-data'@'localhost' (using password: YES)

I haven't created any users or set any passwords or done anything, all I'm doing is going to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and it comes up with the login page.

Can someone please help?

I'm running Ubuntu 7.04 (64-bit) and I got phpmyadmin from the synaptic package manager.

thanks.

---

### Post by pheeror on 2007-10-02
Mysql server gives you this error. You (www-data) don't have permission to that database. Checkout permissions in mysql (database mysql).IIRC Sometimes this can happen, because in mysql localhost means socket not 127.0.0.1.

---

### Post by Arbiter on 2007-10-05
I'm having the same problem.  How do I do this?  I'm not experienced with MySQL and am trying to set up a Gallery2 installation

---

### Post by pheeror on 2007-10-06
```

$mysql -u root -p
mysql> use mysql;
mysql>select * from mysql.user;
mysql> select * from db;

```
And check out what permissions you have setted (this is probably grammaticaly incorrect ;-))

You can create new database
```

create database DATABASE

```
and set permissions with
```

grant all privileges on DATABASE.* to 'USER'@'HOST' identified by 'PASSWORD';

```
HOST is ip address or hostname, if you use %, database can be accessed from everywhere.

You can also change permissions in table db or user with standard mysql commands and then run
```

flush privileges;

```

---

### Post by Arbiter on 2007-10-08
I just tried granting all privleges on the database to www-data and phpmyadmin still won't let me in, even using the password i specified.

---

