---
title: "Harddrive not found"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by nodger on 2010-11-20
I've built a new computer and successfully installed XP on it. I've tried to install Ubuntu 10.04 64-bit edition from a pen drive and CD. I can boot into the pendrive and use it however when I try to install it doesn't recognize the harddrive.

At the moment there are no jumpers on the harddrive although I've tried them in several positions to no avail. I've also tried plugging the harddrive in several of the SATA ports on the motherboard. I even tried unplugging the DVD drive altogether.. no joy. I also went into the Bios and changed the mode to AHCI (it was set to IDE)

My motherboard is a Asus P6X58D-E with an i7 processor and 2Gb ram.
The harddrive is a 500Gb WD5000AAKS

please, please help.

---

### Post by nodger on 2010-11-21
bump

---

### Post by dino99 on 2010-11-21
Set the bios to ahci or better to "compatible" if this choice exist, and check the boot order and settings.
Read the motherboard doc about sata and plug order, read the hdd doc.

here is how to format to install ubuntu:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by sikander3786 on 2010-11-21
> I've also tried plugging the harddrive in several of the SATA ports on the motherboard.

If the motherboard has more than one Sata controllers, plugging the HDD to the other controller might help. (They look like 2 different coloured groups of Sata Ports on the board).

---

### Post by Eufouria on 2011-01-14
I've just installed ubuntu on this same MB and I'm using up both SATA controllers. Ubuntu isn't recognizing the 2 drives on the second controller. 

Could it be possible drivers aren't available yet because it's a newer 6 GBps controller? It's been out a year...

---

### Post by Eufouria on 2011-01-14
*

---

### Post by Eufouria on 2011-01-14
*

---

### Post by Eufouria on 2011-01-14
Sorry, forums acting strangely in Opera under ubuntu.

---

