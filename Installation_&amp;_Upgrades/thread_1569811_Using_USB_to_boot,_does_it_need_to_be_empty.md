---
title: "Using USB to boot, does it need to be empty?"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by aNDoz on 2010-09-07
also, what size does the usb have to be?

---

### Post by Skaperen on 2010-09-07
Depending on what you will be doing to make the USB memory stick bootable, it may wipe out what is already there.  And in some cases what is already there can interfere with making it bootable or making it work right.  Starting with an empty USB memory stick insures that you won't be losing files you wanted to keep, and won't risk corrupting what you are about to put on there.

The size needed depends on what you need to put on there.  A full install of Ubuntu might require 4GB or more.  Making it bootable as a rescue tool or an install tool can take less.  For example, my USB memory stick install images of Ubuntu 10.04 LTS fits in less than 1GB.  A rescue booter that only has a boot loader and kernel, which assumes your host filesystem is OK, can be done in less than 32M.  I bet you can't even find a USB memory stick that small anymore.

Smaller USB memory sticks are cheap.  Get a few.  Put installers on a couple of them.  Put the rescue stuff on a couple more.  Get an 8GB or larger one, and do an install that targets this big one as the hard drive to install onto (makes a slower, but full, system you can boot and run from).  I have such a thing on a 16GB SDHC card for my netbook.

---

### Post by petrus250 on 2010-09-07
No, it shouldn't matter whether or not it is empty, but I would advise a 4 gig if you want to burn ubuntu.

---

### Post by aNDoz on 2010-09-07
I'm using a 4gb drive and I've just wiped it ( all I had one was PS3 stuff)

The "diagnostic messages" program has listed 55 files and says  "file is broken" after them all

this normal?

---

### Post by aNDoz on 2010-09-07
How long is this expected to take? 
It's been 3 1/2 hours!

---

### Post by thegod_slayer on 2010-09-07
> **aNDoz said:**
> 

The "diagnostic messages" program has listed 55 files and says  "file is broken" after them all

this normal?

didn't understand this

please explain

---

### Post by thegod_slayer on 2010-09-07
booting ubuntu from usb takes the same time that it should take from a cd

i would advice you to make the bootable usb from any ubuntu syatme by the usb startup disk creator

---

### Post by C.S.Cameron on 2010-09-07
It is a good idea to check the iso's MD5SUM to make sure your download is good.

---

