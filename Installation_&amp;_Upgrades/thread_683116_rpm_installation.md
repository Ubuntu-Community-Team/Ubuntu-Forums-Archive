---
title: "rpm installation"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by jsentianus on 2008-01-30
I have tried to find the answer to my problem from the posted replied but couldnt get the right one.

My problem is to remove ksh that I have installed before (no longer needed as its affecting the use of pdksh) for I need to install some software for my work. I have been asked to remove the ksh using the following command:

>rpm -e ksh

I have done that but the following error appeared...something to do with rpm installation in alien. I'm asking if anyone could advise me on how to proceed from here as I dont really understand this thing.

sentian@dell:~$ whereis rpm
rpm: /usr/bin/rpm /usr/lib/rpm /usr/X11R6/bin/rpm /usr/bin/X11/rpm /usr/share/man/man8/rpm.8.gz
sentian@dell:~$ rpm -e ksh
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm
error: package ksh is not installed

---

### Post by yabbadabbadont on 2008-01-30
If you installed ksh using the package manger included with Ubuntu, then you would remove it the same way.  System->Administration->Synaptic Package Manger  Then search for ksh and select it for removal.  Or you could use a terminal window and run:
```
sudo apt-get remove ksh
```

---

