---
title: "using external drive as main drive"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by antswilleatrome on 2008-03-10
i recently bought a 500gb external HDD and i'm trying to use it as my main disk, i managed to partition it and install ubuntu on it, but it wont boot, and seeing as this is an older motherboard, it probably does not have boot from USB support.

i have a 40gb internal drive that im not using right now, is it possible to load it first as a boot disk to boot onto the external drive?

another option i considered was using the 40gb internal drive for the OS and having the /home partition on the external drive.

problem is i don't know how do do any of the above or even if it's possible, so if someone could post links to tutorials/step by step guides, it would be much appreciated :)

---

### Post by logos34 on 2008-03-10
Give this guide a shot:

[https://help.ubuntu.com/community/BootFromUSB#head-c56d6ffb96b299d571031b05360d2a43e5769d67](https://help.ubuntu.com/community/BootFromUSB#head-c56d6ffb96b299d571031b05360d2a43e5769d67)

You might also see if [Super Grub Disk]("http://supergrub.forjamari.linex.org/") will boot the usb.  Probably not, but worth a try.  If nothing else you'll end up with an SGD cd--nice thing to have around.

(i'm just assuming your problem is as you said--old mobo doesn't support usb boot)

---

