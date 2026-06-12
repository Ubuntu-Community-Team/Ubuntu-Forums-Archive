---
title: "error removing mysql"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by mosty friedman on 2010-03-15
hey everyone,

I have a problem with mysql, but every time i try to remove it or reinstall i get this error

```

E: /var/cache/apt/archives/mysql-server-5.1_5.1.37-1ubuntu5.1_i386.deb: subprocess new pre-removal script returned error exit status 1

```

I am using ubuntu 9.10 and i was trying to do that from the synaptic package manager...if anyone could help that would be great, coz i have been trying to install mysql for a few days now but it keeps failing

---

### Post by n0dix on 2010-03-15
Do you try with:
```
$ sudo apt-get -f install mysql
```
If don't work try to do a backup of mysql-server-5.1_5.1.37-1ubuntu5.1_i386.deb package, then try again.

---

### Post by mosty friedman on 2010-03-15
that's giving me another error
```

mosty@mosty:~$ sudo apt-get -f install mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package mysql

```

---

### Post by n0dix on 2010-03-15
I mean:
```
$ sudo apt-get -f install mysql-server
```

---

### Post by mosty friedman on 2010-03-15
thanks, that worked..any idea on how to setup the password for mysql??

---

### Post by n0dix on 2010-03-15
Here's the [link]("http://www.cyberciti.biz/faq/mysql-change-root-password/").

---

### Post by mosty friedman on 2010-03-16
actually i am afraid mysql-server-5.1 is broken, i was trying to install openoffice and it gave me an error when setting up mysql, i try to fix the broken stuff by
```

sudo apt-get install -f

```

and its giving me an error

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                             [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.

```

---

### Post by AnthonyBeldt on 2010-03-16
> **n0dix said:**
> Do you try with:
```
$ sudo apt-get -f install mysql
```If don't work try to do a backup of mysql-server-5.1_5.1.37-1ubuntu5.1_i386.deb package, then try again.


This works like a charm, Thanks buddy for your help!

---

### Post by n0dix on 2010-03-16
> **mosty friedman said:**
> actually i am afraid mysql-server-5.1 is broken, i was trying to install openoffice and it gave me an error when setting up mysql, i try to fix the broken stuff by
```

sudo apt-get install -f

```

and its giving me an error

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                             [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.

```

Try with this:
```
$ sudo apt-get purgue mysql-server
```
then installed
```
$ sudo apt-get install mysql-server
```

---

### Post by mosty friedman on 2010-03-17
thank you very much n0dix, i was able to install mysql with no problems..however i have a problem with setting the root password

```

mysqladmin -u root password *****

```
```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

if anyone could help i would really appreciate it..sorry for asking too many questions though

---

### Post by n0dix on 2010-03-17
Did you try with:
```
mysql -u root -p <password>
```
or 
```
mysql -u root -p
```
then write your password

---

### Post by mosty friedman on 2010-03-17
i tried
```

mosty@mosty:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

any fix around this??

---

### Post by n0dix on 2010-03-17
Did you start the daemon?

---

### Post by mosty friedman on 2010-03-17
can't seem to start it
```

mosty@mosty:~$ 100317 18:51:25 mysqld_safe Logging to syslog.
100317 18:51:25 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
100317 18:51:25 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended

```

---

### Post by n0dix on 2010-03-17
What do you get when execute this:
```
$ sudo /etc/init.d/mysqld restart 
```?

---

### Post by mosty friedman on 2010-03-17
```

mosty@mosty:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                             [ OK ] 
 * Starting MySQL database server mysqld                                                                                                             [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
mosty@mosty:~$ ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)

```

any ideas?

---

### Post by n0dix on 2010-03-17
See [this]("http://mirzmaster.wordpress.com/2009/01/16/mysql-access-denied-for-user-debian-sys-maintlocalhost/").

---

### Post by mosty friedman on 2010-03-17
still no luck as i cant set the root password thus i cant logon as root

---

### Post by n0dix on 2010-03-17
Setting again the root password, [link]("http://www.ubuntugeek.com/reset-the-root-password-on-mysql.html").
Then, try again.

---

### Post by mosty friedman on 2010-03-17
thank you very very very much n0dix..resetting the root password finally worked and i can now login as root..thanks again, I have learned a lot in this process.

---

### Post by n0dix on 2010-03-17
me too. ;)
Don't forget to add Solved to the title.

---

### Post by ben.walker on 2010-03-22
> **n0dix said:**
> Try with this:
```
$ sudo apt-get purgue mysql-server
```then installed
```
$ sudo apt-get install mysql-server
```


It is working. My Sql server problem sorted out.

---

### Post by peter.hopkins on 2010-03-25
Thanks for sharing this info. From last 3 days i am suffering with this issue. At last i sorted out. Thanks to my friends Gavin who suggest me this forum.

---

### Post by jaya28inside on 2010-08-19
sorry guys... i'm waking up the thread again...

but I encounter the same problem,
many things stuck 
and error and so on...
now I also want to remove mysql-server from my ubuntu server

but,,, before removing it,
i try to restart using

```

root@omega:~# /etc/init.d/mysql restart

```

I juz got

```

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart mysql

```

what should I do to remove it now?
I got this happened again and again... not successfully removing it yet

---

