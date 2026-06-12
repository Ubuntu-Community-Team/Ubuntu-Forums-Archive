---
title: "installer"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by baluselva on 2011-12-16
is it enough to install wubi installer to install ubuntu 11.10 along windows 7..?
that installer is having a size of just 3mb only..do i need to download and install
 the whole ubuntu os of size 700mb..?

---

### Post by hansdown on 2011-12-16
Welcome to the forum, baluselva.

I've never done a wubi install, but you can test ubuntu with a live disc.

[http://ubuntu.paslah.com/ubuntu-live-cddvdusb/](http://ubuntu.paslah.com/ubuntu-live-cddvdusb/)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Choose 32bit, or 64 bit.

---

### Post by mikewhatever on 2011-12-16
Yes, wubi will download the 700MB ISO for you.

---

### Post by bcbc on 2011-12-17
From release 11.10 onwards, wubi.exe will download a ~500MB preinstalled image that is expanded onto the virtual disk, removing the need for a second stage install. 

It's still possible to install Wubi the old way, by downloading the 700MB desktop CD ISO yourself and placing it in the same folder as wubi.exe, or burning a CD and running wubi from that.

There are a couple of differences between the two methods. The preinstalled image method won't work on FAT32 partitions [lpbug]882393[/lpbug] and gives false errors in some cases [lpbug]862003[/lpbug]

---

