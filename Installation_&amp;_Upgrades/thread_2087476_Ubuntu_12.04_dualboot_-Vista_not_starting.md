---
title: "Ubuntu 12.04 dualboot -Vista not starting"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by canuck11 on 2012-11-23
Hi,

Your help would be appreciated.

I am running a Clean Install of Ubuntu 12.04 AMD 64 Bit with Vista.

I have the following problems...

[1] Vista Does not Boot anymore (endless reboot Vista MBR must be damaged somehow)

[2] Ubuntu 12.04 with updates Boots Only with Grub2 CD in Optical Drive of this laptop

[3] Can not Boot Ubuntu via Grub2 even after Boot Repair.

My Boot-Repair Info...[http://paste.ubuntu.com/1380498/](http://paste.ubuntu.com/1380498/)

This must be a relatively easy fix since...

I can Boot via Grub2 CD press enter twice and it launches Ubuntu 12.04 AMD 64 Bit off a Partition (sda6) off my Hard Drive (not a Live CD of Ubuntu).

---

### Post by canuck11 on 2012-11-23
Hi,

I have a similar problem can you help me?

[1] Grub2 installed with Vista + Ubuntu 12.04 AMD 64 Bit

[2] Vista does not boot anymore (it did before)

[3] This is a Clean install of 12.04 AMD 64 Bit

[4] Can only boot with Grub2 Boot CD in Optical Drive-that boots 12.04 off HDD!

Any Ideas? Tried Boot-Repair did not work perhaps I am selecting the wrong options?

Boot Info...

[http://paste.ubuntu.com/1380498/](http://paste.ubuntu.com/1380498/)

---

### Post by oldfred on 2012-11-23
Moved to your own thread.

With gparted move boot flag or Windows active partition back to sda2. Grub does not use boot flag, but Windows will only boot, repair or install to the NTFS primary partition with the boot flag.

And did you change the size of the Vista partition? It has some size  issues and often chkdsk from a Windows repairCD will fix that on sda2.

Grub2's boot loader should not be installed to partitions PBR and never to NTFS partitions. NTFS partitions have Windows boot code and other NTFS internal data. NTFS does keep a backup partition boot sector or PBR which with testdisk you can restore. Use this on sda1 which is your recovery partition. 

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by oldfred on 2012-11-24
You had a post in another thread & I moved it to its own thread. Then it looks like you did create your own thread. Merged them together.

---

