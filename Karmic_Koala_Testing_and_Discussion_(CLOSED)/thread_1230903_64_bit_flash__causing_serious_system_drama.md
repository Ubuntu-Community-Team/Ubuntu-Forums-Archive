---
title: "64 bit flash  causing serious system drama"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-08-03
This is a fresh install of Karmic 64 bit. I tried to install flash from Adobe and it failed horribly. Now I can not update any thing until I get this 'broken' package removed.
I did manage to get flash working as youtube videos do work great.
So please, some one help me fix this:
```
Preparing to replace libc6 2.10.1-0ubuntu1 (using .../libc6_2.10.1-0ubuntu2_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.10.1-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.10.1-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.10.1-0ubuntu2); however:
  Version of libc6 on system is 2.10.1-0ubuntu1.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-i386
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

```

---

### Post by dinxter on 2009-08-04
fuser -v /var/cache/debconf/config.dat

should show you what (if any) process is locking it
possibly a stalled debconf from a previous dpkg going bad

---

### Post by dino99 on 2009-08-04
may be give a try to getlibs

---

### Post by novafluxx on 2009-08-04
May I suggest, instead of using the 32-bit flash with the wrapper, just using the native 64-bit flash library. I never had any problems using it before, and I heard Adobe just released a new refresh of the native 64-bit Linux version of Flash.

---

### Post by DougieFresh4U on 2009-08-04
Any 'sudo' magic for the terminal to force this mess away?
(can hardly wait for the jokes)

---

### Post by Riffer on 2009-08-18
Same problem as you, upgraded to Karmic and Flash was broken.  Found this replacement Flash plugin for 64 bit, works a treat for me.  

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

It requires you to manually place the plugin into the correct folder but isn't very clear on exactly what folder.  I found on mine that the folder is   /usr/lib/mozilla/plugins/.

Good Luck

---

