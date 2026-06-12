---
title: "Problems upgrading MySQL"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by period3 on 2007-04-30
The ubuntu update manager says there's an upgrade for mysql-server 5.0... WHen I try to apply the upgrade, I get:  E: /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb: subprocess new pre-removal script returned error exit status 1

Any thoughts on how to fix this?  The text of the output is:


Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 108792 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.24a-9 (using .../mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ ok ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.24a-9ubuntu2_all.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.24a-9ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server (5.0.24a-9ubuntu2) ...


Thanks

---

### Post by superyounan1 on 2007-04-30
I have a similar problem... a couple weeks ago i shut the lid on my Laptop, and when I opened it, the screen wouldnt turn on again and the system didnt look like it was responding.

I powered off the laptop and when I booted again, i got some very cryptic messages (dont remember exactly what) that told me to manually run some sort of disk checking utility, which I did. It found a whole bunch of errors, and when I restarted all was well again, EXCEPT mysql. I could no longer log in and kept getting 

```
error: 'Access denied for user 'debian-sys-maint'@'localhost' 
```

i tried doing a complete purge and reinstall of mysql, but that did not help, and naturally after the feisty upgrade, i had problems with it again.

I havent found a good way to fix it yet, if you do figure it out or if someone else knows, please post here.

---

### Post by secutus on 2007-05-02
Dear,

Solution (well in my case it worked): 

first stop the mysql-server and then perform the upgrade.

Kind regards
Secutus

---

