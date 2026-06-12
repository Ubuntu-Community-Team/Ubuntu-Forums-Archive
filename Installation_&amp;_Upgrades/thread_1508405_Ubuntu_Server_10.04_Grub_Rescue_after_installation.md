---
title: "Ubuntu Server 10.04 Grub Rescue after installation"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Mustardo on 2010-06-12
Hey all.

**Situation:** Fresh install (using entire disk)of Ubuntu Server 10.04 and boots to Grub rescue prompt

What I can't understand is if I place the hard drive into another box it will boot fine.

I have tried every arrangement of Primary / Secondary Master configurations and still to no avail.  Although I assume grub is at fault as it at least gets to the MBR in order to produce the Grub Rescue prompt?

I have also tried reinstalling GRUB from the live CD

**Systems: **  Pentium 1, other machine (that works) is a Pentium 4.

Please let me know if I could post any other information that 
would help resolve this.  I'm out of ideas.

I'm currently booting a live CD to run the [boot info script]("http://bootinfoscript.sourceforge.net/")

Thanks in advance.

---

### Post by Mustardo on 2010-06-16
I have solved this problem by making a separate < 8GB partition to install the Operating System on.  It seems that the BIOS was not able start executing a Kernel on a partition > 8GB (I think some older boards are limited to 512MB)

I will post some more information and details soon for anyone else who may fall into this trap playing with old/ancient hardware.

---

