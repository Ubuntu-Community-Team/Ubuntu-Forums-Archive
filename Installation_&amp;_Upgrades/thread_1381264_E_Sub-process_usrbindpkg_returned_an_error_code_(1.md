---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by The Toxic Mite on 2010-01-14
Hey!

I'm trying to install a few packages onto my Ubuntu partition, but when I try to do so, /usr/bin/dpkg returns the above error.

Can anyone tell me what's going on here?

```

$ sudo apt-get install linux-source-2.6.31
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-source-2.6.31 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up rt2870-linux-sta (2.1.2.0-0ubuntu2) ...

Error! DKMS tree already contains: rt2870-linux-sta-2.1.2.0
You cannot add the same module/version combo more than once.
ERROR: dkms add failed.
dpkg: error processing rt2870-linux-sta (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rt2870-linux-sta
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

You may also want the contents of my /etc/apt/sources.list :

[http://paste.ubuntu.com/356739/](http://paste.ubuntu.com/356739/)

---

