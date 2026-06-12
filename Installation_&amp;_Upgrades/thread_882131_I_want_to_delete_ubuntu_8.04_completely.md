---
title: "I want to delete ubuntu 8.04 completely"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Millie da kidd on 2008-08-06
I am not dual booting it with nothing.
Ubuntu 8.04 is the only operating system i have on my acer.
i want to delete it completely so i can use my acer system restore disk.
thank you in advance

---

### Post by raul_ on 2008-08-06
You could use the Partitioner included in the Live CD to wipe out that partition, or just reinstall Windows and let it use the whole disk.

Why can't you use the Restore disk anyway?

---

### Post by SarahKH on 2008-08-06
The restore disk(s) should just wipe the drive and go at it again, including removing any trace of GRUB from the MBR. 

However.  On the off chance it doesn't, grab any form of LiveCD (like the Ubuntu one you might still have kicking around) and once booted fire up gparted.

In there just delete everything on either /dev/sda or /dev/hda (usually, double check that though, your machine could be weird), format as a single large FAT32 partition and set the boot flag; that should be sufficient to get even the dumbest restore CD going I'd have thought.

---

### Post by wpshooter on 2008-08-06
Get [www.killdisk.com](www.killdisk.com) to WIPE it clean.

---

### Post by philetus on 2008-08-06
I still boot up with a floppy and go to fdisk.
Me and DOS,old.

---

