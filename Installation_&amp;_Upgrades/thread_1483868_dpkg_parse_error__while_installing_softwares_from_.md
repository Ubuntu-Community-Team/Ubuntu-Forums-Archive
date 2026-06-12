---
title: "dpkg: parse error : while installing softwares from command line"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by mantosh4u on 2010-05-15
Hi,

I was trying to install " evince "  on my ubuntu platform.

But i am getting this error everytime...


mantosh@ubuntu:~$ sudo apt-get install evince
[sudo] password for mantosh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evince is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 68 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
[B]dpkg: parse error, in file `/var/lib/dpkg/available' near line 20978 package `kdelibs5':
 field name `Original-Maintain_wm9712.c' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]



Please let me know, what shall i do to avoid this error.

Regards,
Mantosh:guitar:

---

### Post by dv3500ea on 2010-05-15
It looks like evince is already installed.
I'm not sure about the error.
Try running
```
sudo apt-get install -f
```

---

