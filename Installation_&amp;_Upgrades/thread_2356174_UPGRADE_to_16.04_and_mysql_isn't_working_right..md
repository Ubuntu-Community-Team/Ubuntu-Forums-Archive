---
title: "UPGRADE to 16.04 and mysql isn't working right."
date: 2017-03-20
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-03-20
I upgraded a server to 16.04 and it didn't go well. I have all of the errors cleaned up but one application, Egroupware is not working. It seems there is a problem with be mysql database that holds all of the data.

This all worked fine before I upgraded.
I can open the database and look at the tables but the designated user (egroupware) can not access the database.
Here is some of the output from some basic mysql commands

> #mysql -u root -p
 mysql> SELECT host, user FROM mysql.user ;
 +-----------+------------------+
 | host      | user                      |
 +-----------+------------------+
 | hamlet    | root                     |
 | localhost | debian-sys-maint    |
 | localhost | egroupware           |
 | localhost | mysql.sys              |
 | localhost | root                     |
 +-----------+------------------+
 5 rows in set (0.00 sec)


 mysql> SHOW GRANTS FOR 'egroupware'@'localhost';
 ERROR 1141 (42000): There is no such grant defined for user 'egroupware' on host 'localhost'

 mysql> GRANT ALL ON *.* TO 'egroupware'@'localhost' WITH GRANT OPTION;
 ERROR 1133 (42000): Can't find any matching row in the user table

---

### Post by yancek on 2017-03-20
Don't you need 'privileges' in the command: GRANT ALL PRIVILEGES ON...

---

### Post by QIII on 2017-03-20
I think your clue is here:

```
ERROR 1133 (42000): Can't find any matching row in the user table
```

See if that user exists:

```
SELECT User FROM mysql.user;
```

Is "egroupware" there?

---

### Post by alexandari on 2017-03-21
Might be related to the fact that Ubuntu 16.04 comes with Mysql 5.7. It's slightly different than the older versions, check if Egroupware supports it

---

### Post by rsteinmetz70112 on 2017-03-21
> **QIII said:**
> I think your clue is here:

```
ERROR 1133 (42000): Can't find any matching row in the user table
```

See if that user exists:

```
SELECT User FROM mysql.user;
```

Is "egroupware" there?

I posted the results of that in my initial post. See the first message in the thread.
> 
mysql> SELECT host, user FROM mysql.user ;
+-----------+------------------+
| host | user |
+-----------+------------------+
| hamlet | root |
| localhost | debian-sys-maint |
**| localhost | egroupware |**
| localhost | mysql.sys |
| localhost | root |
+-----------+------------------+
5 rows in set (0.00 sec)

---

### Post by rsteinmetz70112 on 2017-03-21
Thanks. I figured it out after my first post. A lot of the stuff out there doesn't exactly apply to 5.7 

> **yancek said:**
> Don't you need 'privileges' in the command: GRANT ALL PRIVILEGES ON...

I do but adding it didn't help:

> 
mysql> GRANT ALL PRIVILEGES ON egroupware.* TO 'egroupware'@'localhost';
ERROR 1133 (42000): Can't find any matching row in the user table

I created another USER and ran this same command and it worked. There seems to be something wrong with this user.

---

### Post by rsteinmetz70112 on 2017-03-21
Thanks to everyone who helped.

I was able to get it fixed.

I CREATEed a new USER. Switched the Egroupware to that user then I was able to DROP the 'egroupware' USER and Create a NEW one. I was then able to GRANT PRIVILEGES to the "new" 'egroupware'.

Somehow the "old" 'egroupware' was not recognized by any of the commands except DROP.

---

