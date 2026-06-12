---
title: "Dual Booting problem"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by nkessler2000 on 2005-08-24
I'm having some issues dual booting my system. I have two hard drives, a SATA drive with Windows installed on it, and an IDE drive with Ubuntu. With the way things are now, If I want to boot into Windows, I have to go into the BIOS and change the first boot device to SCSI. If I want Ubuntu I have to change it to IDE. 

The Ubuntu installer sucessfully detected the Windows installation on the SATA drive, and added an entry for it in GRUB. It is set to boot off (hd1,0). However, when I select that from the GRUB menu, the system just hangs. 

So I tried doing it the other way around, using the Windows boot loader to boot Ubuntu, following [this guide](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html). However, when I try to boot Ubuntu that way, the screen just says GRUB and hangs. The guide says that may be caused by my boot partiton (which is /dev/hdb3 in my case) being above cylinder 1024. Short of repartitioning my drive, is there anything else I can do?

Any ideas on how I can get it to work either way? Lemme know if you need any more info.

---

