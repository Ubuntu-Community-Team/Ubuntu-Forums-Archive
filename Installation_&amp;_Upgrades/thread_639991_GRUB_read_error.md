---
title: "GRUB read error"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by kavoura on 2007-12-13
I have a PC which has Xandros Linux on it, which uses LILO boot loader, but that failed to load when I rebooted the PC earlier today.
So I decided to boot from an Ubuntu 7.10 live DVD, and then install Ubuntu to a spare partition. Now when I boot the PC from the hard disk, I get an error saying "GRUB read error" and the system hangs, nothing else is possible other than rebooting. I can boot from CDs/DVDs but not the hard disk.
What can I do to fix this?
I have tried reinstalling GRUB from the live Ubuntu using instructions I found elsewhere on this forum, but that did not work.

---

### Post by logos34 on 2007-12-13
Sounds like the hard disk is no longer being detected properly/Bios settings have changed.  Have a look in the bios at startup

---

### Post by kavoura on 2007-12-14
I booted from a CD called the Ultimate Boot CD and ran the Seagate SeaTools program, and it found a number of errors on the hard disk, which it repaired.
Then I rebooted the PC and GRUB worked, so I was then able to boot into Ubuntu. Although as it starts up Ubuntu finds some problems with the hard disks and that will have to be resolved. I plan to replace the two that have faults with a different larger hard disk and transfer all the partitions/data to the new disk. Hopefully that will make everything run better.

---

### Post by logos34 on 2007-12-14
so it was bad sectors and/or physical damage...that possibility should have occured to me right away.  

Look into [partimage]("http://www.partimage.org/Main_Page") or [clonezilla]("http://clonezilla.sourceforge.net/").

---

