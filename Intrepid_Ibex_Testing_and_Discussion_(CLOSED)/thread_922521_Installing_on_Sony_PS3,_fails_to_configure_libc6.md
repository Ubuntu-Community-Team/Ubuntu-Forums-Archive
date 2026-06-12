---
title: "Installing on Sony PS3, fails to configure libc6"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ardrias on 2008-09-17
As the topic says, I've tried to install the latest build of the PS3 port, but it keeps failing to configure libc6... thus ending the install. I thought I had corrupted media (I'm cheap, I use RW and they get dirty), but I've tried changing that too.

So... what could be wrong?

---

### Post by Tuig on 2008-09-17
the ps3 version is still a bit rough.

more information is here:
[http://psubuntu.com/forums/viewtopic.php?f=4&p=1840](http://psubuntu.com/forums/viewtopic.php?f=4&p=1840)

A week ago, the daily build did install (with quite a few warnings).
I installed petitboot beforehand, and manually installed the kernel
from:
[https://lists.ubuntu.com/archives/ubuntu-cell/2008-September/000179.html](https://lists.ubuntu.com/archives/ubuntu-cell/2008-September/000179.html)

installing kde fails but after rebooting, at least 'apt-get' is there, so 'apt-get install kubuntu-desktop' makes it all work.
I use xubuntu, since it uses less ram.

---

### Post by Shin_Gouki2501 on 2008-09-17
KDE 4.1 faster then gnome, ho ;)

---

### Post by Ardrias on 2008-09-18
Meh I'll try and tinker a bit with this during the weekend I suppose. The idea is that the final release will install just fine tho, right? As in... straight from the .iso, no extra faffing about needed.

---

### Post by Nullack on 2008-09-18
If you look through the debugging section of the Ubuntu wiki on bug reports, you may not find the solution but you'll get some pointers on how to look at certain logs and grab info on the system. That will all help make fixing it easier.

---

### Post by Ardrias on 2008-09-18
> **Nullack said:**
> If you look through the debugging section of the Ubuntu wiki on bug reports, you may not find the solution but you'll get some pointers on how to look at certain logs and grab info on the system. That will all help make fixing it easier.

Any tips where to start looking for stuff? Seeing as the installer dies quite early, there's not really much to be found...

If I read through /var/log/syslog I can see something like: 
```

dpkg: error processing initscripts (-configure):
 subprocess post-installation script returned error exit status 32
Errors were encountered while processing:
 initscripts
Setting up initscripts (2.86.ds1-59ubuntu5) ...
mount: unkown filesystem type 'spufs'

```

It seems like it's this problem I'm having [https://bugs.launchpad.net/ubuntu-ps3-port/+bug/251593](https://bugs.launchpad.net/ubuntu-ps3-port/+bug/251593)

Just hope it gets fixed quick enough... I'll happily test it :D

---

