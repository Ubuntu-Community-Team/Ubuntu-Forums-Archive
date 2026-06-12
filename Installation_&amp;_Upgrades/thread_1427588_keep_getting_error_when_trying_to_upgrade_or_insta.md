---
title: "keep getting error when trying to upgrade or install"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by schenier on 2010-03-11
I tried to fix the broken dependencies and it still gives me this error message in the end :

Unpacking libusbmuxd1 (from .../libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libusbmuxd.so.1.0.0', which is also in package libusbmux0 0:1.0.0-rc1-1ubuntu3~k
Errors were encountered while processing:
 /var/cache/apt/archives/libusbmuxd1_1.0.1-0ubuntu1~k_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am still a beginner at Linux. Could someone help me please.

All this happened after I tried to install some package so Ubuntu could synch with my iPod

Thanks

---

### Post by jjcv on 2010-03-11
This is a good way to fix broken packages:

sudo apt-get -f install

You'll be pleased to know that syncing with your ipod comes with the next version of Ubuntu (10.4) which is in Alpha 3 testing now.

---

### Post by schenier on 2010-03-12
I read that yes. Can't wait. And the error message I got and copied in my previous message was after I did the 

sudo apt-get -f install

if it can help someone to find what may have gone wrong, here is the URL that I was following instructions from. I got errors after I did the step 3 .

[http://www.mexlinux.com/how-to-sync-music-between-iphone-and-ubuntu/](http://www.mexlinux.com/how-to-sync-music-between-iphone-and-ubuntu/)

thanks.

---

### Post by schenier on 2010-03-12
somehow, when I tried to install another program through synaptic, it finally corrected the problem and I am OK now.

:D

---

