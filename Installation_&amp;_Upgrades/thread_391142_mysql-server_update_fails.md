---
title: "mysql-server update fails"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by bananabob on 2007-03-22
I can not complete an update of mysql-server. I get the following error messages from the update manager. Any clues on how to fix this please.

> 
Preconfiguring packages ...
(Reading database ... 134444 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.24a-9 (using .../mysql-server-5.0_5.0.24a-9ubuntu0.1_i386.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ ok ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:



---

### Post by wwuster on 2007-03-23
It's failing for me too.

William

---

### Post by Arby on 2007-03-23
there seem to have been a lot of errors with mysql updates recently. I don't know why. This thread [http://www.ubuntuforums.org/showthread.php?p=1970459](http://www.ubuntuforums.org/showthread.php?p=1970459) describes a very similar problem and how to fix it. So you might have some luck there. The other thing that's cropping up a lot lately is this one [http://sidux.org/PNphpBB2-viewtopic-t-78.html](http://sidux.org/PNphpBB2-viewtopic-t-78.html) So that might be worth a look as well.

have a look at those and let us know how it works out.

Hope it helps

Arby

---

### Post by milton1 on 2007-03-23
I had the exact same problem as bananabob. This fixed it:

> **Kochin said:**
> Find your debian-sys-maint password in /etc/mysql/debian.cnf.

Then use
```
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;
```
Replace <password> with your debian-sys-maint password.

---

### Post by linuxbz on 2007-03-23
That worked for me.  Thanks Milton1.

---

### Post by somafm on 2007-03-27
Thanks milton1! Worked for me too. :guitar:

---

### Post by bananabob on 2007-03-27
I have a problem with this command.
When I try to run mysql i get the following messahe
> 
bananabob@thorium:~$ mysql
ERROR 1045 (28000): Access denied for user 'bananabob'@'localhost' (using password: NO)
 

So how do I run this GRANT command???

---

### Post by bananabob on 2007-03-30
Ok guys you canforget my last post. I managed to get the command through phpmyadmin. 

Everything works well now.

Thanks for those who suggested the command in the first place.

---

### Post by rayde on 2007-04-11
This worked for me as well.  Any idea why this privilege needs to be manually granted? :confused:

---

