---
title: "I can't get mysql-server-5.0 uninstalled!"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by markg85 on 2008-06-05
Hi,

I used to use Fedora up until a few weeks ago and now try ubuntu. If i had a package that was corrupted or just not working i would do: rpm -e --nodeps packagename

And it would be gone.
I did some research about it for ubuntu and found that it had nearly the same options but i still can't get rid of it.

I'm getting:
```

Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                                                                                                                                                   [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--remove):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                                                                                                                                                   [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                                                                                                                                                   [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0

```

What i actually want to do is install a update.. now that doesn't work due to this same error! Now i just want to get rid of mysql completely and install it again.

I tried all the obvious ways in synaptec and tried a bunch of dpkg commands to remove it but i keep getting the same darn result!

Is there someway that i can let ubuntu forget that it has mysql installed and simply overwrite it? or any other way of getting rid of it without reinstalling ubuntu (if that's the case then my ubuntu adventure probably ends here :P)

Help would be much appreciated.
Mark

---

### Post by Partyboi2 on 2008-06-05
Have you tried 
```
sudo apt-get remove --purge mysql-server-5.0
```
I had a similar problem and this did the trick for me.

---

### Post by markg85 on 2008-06-06
> **Partyboi2 said:**
> Have you tried 
```
sudo apt-get remove --purge mysql-server-5.0
```
I had a similar problem and this did the trick for me.

Sadly it didn't do the trick here..
```
mark@mark-laptop:~$ sudo apt-get remove --purge mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mysql-server-5.0*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 86.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 202369 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                                                                                                   [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing mysql-server-5.0 (--purge):
 subprocess pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                                                                                                   [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                                                                                                   [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@mark-laptop:~$ 

```

---

