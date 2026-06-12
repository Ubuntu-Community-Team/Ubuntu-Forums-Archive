---
title: "Install One Ubuntu Version from ISO of Another?"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by klausner on 2010-05-14
If I'm booted into Ubuntu version X from /dev/sda, and have an ISO image of version Y mounted (using Gmount-iso), or have a CD of Y, can I install Y to /dev/sdb without booting Y?

---

### Post by klausner on 2010-05-17
Bump.

---

### Post by oldfred on 2010-05-18
You can use grub2 to loop mount an ISO and then run it. While the links are for USB it can be done from another partition. You just have to be careful of what partitions are mounted.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

---

### Post by gordintoronto on 2010-05-18
Yes, you can run USB Administration/Startup Disk Creator, point it at an ISO on your system, and create that version of Linux. You don't have to mount the ISO, maybe you should not mount the ISO.

I downloaded the Lubuntu ISO and did exactly this, to get a persistent flash drive which boots Lubuntu.

---

### Post by gordintoronto on 2010-05-18
> **oldfred said:**
> You can use grub2 to loop mount an ISO and then run it. While the links are for USB it can be done from another partition. You just have to be careful of what partitions are mounted.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

This is much more complicated than the simple solution, USB Startup Disk Creator.

---

### Post by oldfred on 2010-05-18
Yes it is more complicated the first time. 

But I have 4 copies of Ubuntu, gparted, system rescue and one or two more, all one one USB. I can update by just copying the ISO over and editing grub.

---

