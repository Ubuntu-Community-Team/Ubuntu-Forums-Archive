---
title: "Startup Disk Creator"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by TopEnder on 2011-08-29
I been following the problems Forum members are having using Startup Disk Creator when trying to create a Bootable USB stick OS mainly with Ubuntu 11.04.

I have tried to use the version installed on both Ubuntu 11.04 Natty & Linux Mint 11.04  and both give the same boot error "Vesamenu.c32 not a com32r image".

Using the version of Startup Disk Creator installed with Ubuntu 10.04 Lynx (LTS) I can successfully create a Bootable USB OS from either a CD image or a Disk image.  

I have created, used and then erased the following versions:

Ubuntu 10.04,
Ubuntu 10.10, and
Ubunt & Linux Mint11.04.  
All the above bootup like the Live CD and have been  booted on different PCs.

From my experience it's not the USB stick but the the version installed with later release of Ubuntu & Linux Mint.

---

### Post by coffeecat on 2011-08-29
> **TopEnder said:**
> 
From my experience it's not the USB stick but the the version installed with later release of Ubuntu & Linux Mint.

You're right. This is a known issue if you use the 10.04 startup disk creator to create a 10.10 usb stick, or vice versa. It seems to involve 11.04 as well. 

A couple of relevant bug reports with some workarounds here:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/686041](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/686041)

[https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818](https://bugs.launchpad.net/ubuntu/maverick/+source/usb-creator/+bug/645818)

---

