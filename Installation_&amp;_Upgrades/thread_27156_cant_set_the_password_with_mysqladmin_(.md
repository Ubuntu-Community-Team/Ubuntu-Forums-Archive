---
title: "cant set the password with mysqladmin :("
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by T31 on 2005-04-15
Hi, thx for reading

This is my problem when I type 

sudo mysqladmin -u root password ********

I get this error message

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'


Ive been trying giving a password to my root, and even getting as root with the su command, but the results are always the same, any idea? ](*,) 

thx again

---

### Post by chaitatp on 2005-04-15
You should try the following instead.

$ sudo mysqladmin -u root -p

And then, it will prompt you to enter the password of mysql.

---

### Post by T31 on 2005-04-15
thx for so quick answer but doesnt work :(

the result i got is like if i just type mysqladmin listing me all the options

what can be wrong in my system? :(

so I tried like this 

root@wawa:/home/t31 # mysqladmin -u root --password *****

Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'

and after reinstall everything, like this

t31@wawa:~ $ sudo mysqladmin -u root -p ******
Password:
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: YES)'


as u can see same error but this time saying (Using password: YES)

I have no idea really :P

---

### Post by chaitatp on 2005-04-15
I'm so wonder if you've ever used ``mysql''?  What do you want ``mysqladmin'' to do? You should use ``mysql'' to connect to the mysql database server, you know.

So what I ask is like ``Do you just want to connect to mysql database server and do some database&table manipulation things?''.... :D

---

### Post by T31 on 2005-04-15
Im starting with php and i want to try a nice cms but i need to build the site locally so i need to install mysql apache and php4 in order to make a local website in my hdd but i cant make mysql run :P

---

### Post by speedman on 2005-04-15
For a fresh mysql install:

mysql -u root -p

<enter> <enter>

SET PASSWORD FOR root = PASSWORD('password_here');

quit

Replace password_here with whatever password you wish to declare.

HTH


Regards,

SM

---

### Post by T31 on 2005-04-15
root@wawa:/home/t31 # mysql -u root -p
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)

root@wawa:/home/t31 # mysql -u root -p
Enter password:
ERROR 1045: Access denied for user: 'root@localhost' (Using password: YES)

using or not password always same results  ](*,)

t31@wawa:~ $ ps xa | grep mysqld
14214 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
14250 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
14251 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
19888 pts/0    S+     0:00 grep mysqld
t31@wawa:~ $

---

### Post by speedman on 2005-04-15
I would suggest starting with a fresh mysql install:

dpkg -l|grep mysql

sudo apt-get remove --purge <all_pkg_names_from_the_command_above>

sudo apt-get install mysql-server-4.1 mysql-common-4.1 mysql-doc

Then follow my instructions above for setting the mysql root password.


Regards,

SM

---

### Post by T31 on 2005-04-15
I cant remove all of them becouse i would remove the metapackage ubuntu-desktop :(

Ive been trying to make a fresh installation as well but few of them are integrated in ubuntu-desktop :( what Ive done is reinstall them, I dunno how many times :(

---

### Post by speedman on 2005-04-15
Try this:

dpkg -l|grep mysql

Note the package names and run this command to avoid the removal of dependant packages:

sudo dpkg -P --force-all <all_pkg_names_from_the_command_above>

Then:

sudo apt-get install <all_pkg_names_from_the_command_above>

Btw, ubuntu-desktop is just a meta package and removing it will not cripple your system.  As a matter of fact I don't have the ubuntu-desktop on my system because it includes evolution-exchange, which is completely unnecessary for me.

HTH


Regards,

SM

---

### Post by T31 on 2005-04-16
solved at last, i had to remove the ubuntu-desktop package and reinstall everything but no works fine

thx a lot for helping xD

---

### Post by speedman on 2005-04-17
Good deal T31.

If you happen to run into this situation again here is a hack that slipped my mind ...

You should have a file generated when mysql is installed here:

/etc/mysql/debian.cnf

The contents will look something like this:

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = xxxxxx

The password line will be much longer than my example above and will contain random alpha numeric characters.

The purpose of this config file is to provide a mechanism for application db updates to be performed by dpkg during a related package upgrade.  However, the credentials above can be used to gain access to a mysql server in the event that the root password has been lost, or forgotten.

Example:

mysql -u debian-sys-maint -pxxxxxx

(Where xxxxxx is the password listed in /etc/mysql/debian.cnf)

Then at the mysql prompt:

SET PASSWORD FOR root = PASSWORD('password_here');

(Where password_here is whatever you want to declare for the root mysql password)

quit (to exit the mysql prompt)

After that you should be able to log in to mysql as root with the password you specified in the step above.


Regards,

SM

---

### Post by chill on 2006-04-07
I don't know if I have exactlythe same problem but.

I have pretty fresh Dapper install. I now installed MySQL Server (and the other things it suggested) and:

```
root@MAREKS:/# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

so I logged in as a debian-sys-maint and:
```
mysql> SET PASSWORD FOR root = PASSWORD('test007');
Query OK, 0 rows affected (0.00 sec)
```

0 rows affected? how about:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost';
ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)
```

I dunno what to do next. How can I log into mysql and have some privileged?

Thanks,

**EDIT:**
I got it working.
I logged into MySql as debian-sys-maint. used database mysql. deleted all users but debian-sys-maint. inserted root used and updated all its rights to 'Y'; and flushed privilegs; Thanks anyway

---

### Post by Abhi Kalyan on 2006-11-04
learning

---

