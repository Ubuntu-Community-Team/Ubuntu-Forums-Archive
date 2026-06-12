---
title: "Grldr error message"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by lakesgirl on 2008-05-23
Have XP on sda1 and Ubuntu 8.04 on sdb1. Not wanting to overwrite the XP mbr on sda, grub 0.97 was installed to the boot sector of sdb1, and I originally booted Ubuntu via a SmartBoot Manager, or sometimes a CAG, floppy.
Recently, just for the experience (being new to Linux) I made a grub boot floppy and also a grub boot CD. Both worked perfectly. 

I decided that it would be convenient if I could get rid of the need for a removeable disk so I copied grldr (v0.4.3) and menu.lst to C:\, and edited my boot.ini accordingly. I now had a choice of boot as expected using XP's loader. However whilst I could sucessfully boot Ubuntu or go back to Windows using the Grub menu, every reference to (hd1,0) produced a warning that the partition table for that disk ie sdb, was not recognized err=115, and please correct using fdisk etc etc. Same applied if I went to the Grub command mode and typed in say, root (hd1,0). 

As I could dual boot from a grub floppy, or a grub CD, without experiencing any warnings I decided to give lode_leroy's grubinstall a try. Essentially, stage1 and stage2 (albeit based on grub v0.93) are copied to C:\boot\ along with menu.lst.  Grubinstall merely sets up the block data. Boot.ini is again modified to suit. This installation works perfectly and is what is presently used.

I can only conclude that grldr looks at the partition table in a different manner to grub itself and in my case is finding something to which it objects, although not seriously enough to prevent Ubuntu sucessfully booting. Does anyone know if grldr's error messages are documented anywhere for if I knew what the objection was maybe I could do something about it?

Note: sdb has 3 primary partitions, ie root, home and swap, followed by an extended partition that has 3 ntfs logical partitions.

---

