---
title: "external disk 7.04 grub bug"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by notidefix on 2007-09-08
when installing ubuntu 7.04 on an external disk, you can set the main boot partition to be hd1 (under advanced options) representing the external disk

consequently, all the grub disk address is of the form hd1,0

unfortunately, when rebooting the external disk is renamed to hd0 which means that you get an  "Error 17 cannot mount selected partition"

easily fixed by re-addressing to hd0,0 (in my case)

although booting off an external hdd is not the primary design for ubuntu, it would be nice if the addresses were consistent during booting from cd and hdd

---

### Post by logos34 on 2007-09-08
actually it's a bios issue (i.e. hard disk boot order)...Your internal IDE or SATA is usually first in the Bios hard disk boot order, ahead of USB-HDD, so it is 'hd0' (the device boot order--cdrom, hard drive, removable--is another thing)....But as soon as you swtich the Bios to boot first to grub on the external USB drive, it becomes hd0, hence the need to change menu.lst root lines to hd0,0. But I agree that soemthing needs to be done to clear up the confusion.  Perhaps a little check box under 'Advanced' for people who are installing ubuntu on USB drives and intend to boot them directly (e.g. notebook users who dual boot).

---

