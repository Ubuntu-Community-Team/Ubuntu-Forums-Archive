---
title: "Ubuntu w/ SATARAID5 Controller - Error 17"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by Laoch on 2007-01-14
I am trying to install Ubuntu 6.10 x64 with a Silicon Image Sil3114 RAID Controller card and 4 

500G Harddrives. I am falling at the first hurdle, I created the RAID Group with the 4 HD in the 

BIOS and then installed Ubuntu 6.10. The HD Layout becomes;

/dev/sda   -  500 GB ATA (RAID Controller)
/dev/sdb   -  500 GB ATA (RAID Controller)
/dev/sdc   -  500 GB ATA (RAID Controller)
/dev/sdd   -  500 GB ATA (RAID Controller)
/dev/sde   -  160 GB ATA

I would have preferred if the 160 GB ATA was /dev/hda but it is not.

I partitioned /dev/sde with 

/        ext3
/swap

to take the OS while I want the 4 on the RAID controller to be seen as one 2 TB partition. 

However before I can even get to installing the SATARAID5 driver I cannot boot the box because I 

ger the following error.

GRUB 1.5
Error 17

---

### Post by ekravche on 2007-01-14
Sometime the order of the drives changes. If you edit your /boot/grub/menu.lst you can change the boot drive id from hd0,1 to hd1,1 for instance, or even to hd2,1. Basically your computer orders the drives and assigns them values from hd0 to hd5 or however man drives you have. So either edit the boot menu during boot or change your boot/grub/menu.lst, so that whichever drive you've installed ubuntu on gets booted first.

---

