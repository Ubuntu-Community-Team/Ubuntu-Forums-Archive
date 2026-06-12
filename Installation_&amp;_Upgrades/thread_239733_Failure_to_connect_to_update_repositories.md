---
title: "Failure to connect to update repositories"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by measdg on 2006-08-19
All of the updating tools (Synaptics, aptitude, apt-get) are having problems connecting to the update servers. They are timing out. My internet connectivity is fine otherwise, it is just the update tools aren't using it or something.

for example:

gmee@gmee-laptop:~$ sudo apt-get update
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun
gmeasday@gmeasday-laptop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done


This is a fresh Ubuntu install. I have not changed my sources.list file so it will still be all of the normal defaults. 

I have tried this:

sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4

which has solved problems with updating for other people but it did not not help me.

Any ideas?

---

### Post by noof on 2006-08-20
Are you sure your connection is working like it should? *au.archive.ubuntu.com* seems to resolve to *1.0.0.0* which is terribly wrong :) try a ```
ping au.archive.ubuntu.com
``` and ```
dig au.archive.ubuntu.com
```

---

### Post by londonbabs on 2006-09-21
[http://ubuntuforums.org/showthread.php?p=1526302#post1526302](http://ubuntuforums.org/showthread.php?p=1526302#post1526302)
check this out, it sorted my problem (although it came back after a system reboot !)

---

