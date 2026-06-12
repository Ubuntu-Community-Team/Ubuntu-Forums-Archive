---
title: "Your basic Dual boot install question"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by under_it on 2007-10-24
Ok, I am almost a complete Linux Noob.  I know enough about it to know that I want to use it, and I have been taking advantage of my works highspeed to download almost every  distro I can get my hands on.  So here is the question.

Last weekend my hard drive died.  I took that chance to partition my new drive so I could dual boot.  I installed Ubuntu ultimate, after the install completed I rebooted and went straight into XP (XP was installed first).  I rebooted to the live cd installed grub.  Rebooted, and grub came up, I booted into XP downloaded some updates rebooted and grub basically died.  I couldnt do anything.  I wound up deleteing the ubuntu partition and rebuilding my MBR to get XP going again.

Later I tried to install opensuse, with no luck the install hangs everytime.  Finally I installed ubuntu, but grub still didnt install is there something I am missing here?

Can someone help me installing grub so that I dont go through the same thing again where I cant boot into anything.

I also found a site saying I could use windows boot selector by modifing my boot.ini file.  that didnt work out to well for me either.

---

### Post by under_it on 2007-10-24
I know there are some distros out there that are system specific.  I have the 64 bit ubuntu.  and I am running a single core 64 bit AMD do I need an AMD specific install?

---

### Post by under_it on 2007-10-26
Ttt

---

### Post by forestpixie on 2007-10-26
I assume it needs to be specific - there are certainly amd64 downloads on the gutsy release - [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

Firstly try using [supergrub]("http://supergrub.forjamari.linex.org/?section=download") to sort the grub error - might be easier than doing it all again. Download it burn as an iso and boot with it.

Hope that helps some

---

