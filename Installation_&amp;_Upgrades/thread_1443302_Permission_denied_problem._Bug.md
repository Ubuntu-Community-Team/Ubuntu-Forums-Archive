---
title: "Permission denied problem. Bug?"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by ArtemNY on 2010-03-30
Reinstalled a fresh copy of Ubuntu 9.10. 

Accordingly to the official manual installed LAMP.

Using:
```
sudo tasksel install lamp-server
```Last step is to change my ip in **my.cnf**.

Opened it with the command terminal.
Tried both:
```
nano /etc/mysql/my.cnf
```
and
```
$ sudo nano /etc/mysql/my.cnf
```

Changed my ip.

Tried to save and:
```
Error writing /etc/mysql/my.cnf: Permission denied
```Tried to manually open **my.cnf**, change my ip and save it and:```

[B][COLOR=Red]Could not save the file /etc/mysql/my.cnf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.[/COLOR][/B]

```I didn't install anything before that, not even updates.
Just installed LAMP on a fresh copy of Ubuntu.

Is this a bug or what?

---

### Post by ArtemNY on 2010-03-30
Can it be possibly  a broken Ubuntu? Maybe it's been downloaded with mistakes?

---

### Post by gmargo on 2010-03-31
What are the permissions on the file and directory?  Even if you're root (via sudo), if the file is read-only, most editors won't overwrite it.  What does "ls -la /etc/mysql/" say?

---

### Post by ArtemNY on 2010-03-31
> **gmargo said:**
> What are the permissions on the file and directory?  Even if you're root (via sudo), if the file is read-only, most editors won't overwrite it.  What does "ls -la /etc/mysql/" say?
That's what I'm trying to learn.

It says: 
```

total 32
drwxr-xr-x   3 root root  4096 2010-03-31 12:53 .
drwxr-xr-x 133 root root 12288 2010-03-31 12:53 ..
drwxr-xr-x   2 root root  4096 2010-03-31 12:53 conf.d
-rw-------   1 root root   333 2010-03-31 12:53 debian.cnf
-rwxr-xr-x   1 root root  1198 2010-02-08 18:56 debian-start
-rw-r--r--   1 root root  3632 2009-10-07 11:44 my.cnf

```
What does that mean? I mean I got it, these all are permissions to files and folder, but why the installation can not overwrite the permission even with sudo?
I reinstalled Ubuntu again with 64-bit but the problem is not fixed.

---

### Post by gmargo on 2010-03-31
There's nothing wrong with the permissions.  I've no idea why you couldn't write to that file.  Can I suggest confusion or too much beer? :p  Just kidding.  Try sudo nano again or try another editor like sudo vim (maybe you have a strange nano setup?)

---

### Post by ArtemNY on 2010-03-31
> **gmargo said:**
> There's nothing wrong with the permissions.  I've no idea why you couldn't write to that file.  Can I suggest confusion or too much beer? :p  Just kidding.  Try sudo nano again or try another editor like sudo vim (maybe you have a strange nano setup?)
Beer can never be too much :p
No it's not a beer...

I reinstalled Ubuntu several times. Used 32 abd 64 bit. Tried to run LAMP installation before and after updates installed. Nothing helps. NOTHING!

Can it be possible some windows-linux confusion? I know I know that it can't but still, I'm checking even impossible choices.

---

### Post by sathyashrayan on 2011-02-15
Ok group,
  I wanted to try the following link..

[http://www.howtogeek.com/howto/database/monitor-all-sql-queries-in-mysql/#comment-118063](http://www.howtogeek.com/howto/database/monitor-all-sql-queries-in-mysql/#comment-118063)

So i did the following and my mysql is not working. Please help..

opened up /etc/mysql/my.cnf. But due non writeable permission i have  changed the my.cnf to “chmod 777 my.cnf”. But the whole mysql is not  working. So again I changed it to -rw-r–r– and still not working. mysql  command gives following error

“ERROR 2002 (HY000): Can’t connect to local MySQL server through socket ‘/var/run/mysqld/mysqld.sock’ (2)”
 Please help. I have lot of data my mysql.

---

