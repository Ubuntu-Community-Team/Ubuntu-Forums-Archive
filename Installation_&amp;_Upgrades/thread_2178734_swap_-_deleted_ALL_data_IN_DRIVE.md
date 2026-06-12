---
title: "swap - deleted ALL data IN DRIVE"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by jordan8 on 2013-10-04
i had 3 drives
W - window7          D  -  data          L-- empty
i booted up my pc with a bootable usb - linux mint 15 cinnamon
tried to install it in the empty drive L
.
it gives 3 options to install  ,,,, i clicked on one saying "SOMETHING DIFFERENT " ( or something like this ) 
during installation i formated my L to ext4 format...i clicked continue .. 
.
the setup said that i have to choose a drive for SWAP MEMORY
I CHOSED MY D DRIVE ( ALL DATA - SOFTS, MOVIES,ALL STUFF ) FOR SWAP MEMORY
.
installation  was successfully completed ....... BUT NOW WHEN I AM BOOTUP MY PC WIN7  START WITHOUT GIVING ANY OPTION TO BOOT MINT..
WIN EXPLORER IS NOT SHOWING DRIVE D and L....  I LOOKED MY RUNNING "MSCONFIG" IT SHOWS ONLY WIN7 AS OS
DISK MANAGER (IN WIN7) SHOWS D DRIVE TO BE 100% FREE...... BUT WHY IT SHOWS L DRIVE TO BE 100%  FREE...
.
PLZ PLZ SUGGEST SOME WAY SO THAT I CAN GET MY DATA BACK (IF POSSIBLE IN - SAME QUALITY)

---

### Post by oldfred on 2013-10-04
**STOP** using computer.

If you have a a fair amount of RAM you may still have your data. Do not boot with Ubuntu live installer is it auto finds swap and uses it to speed up booting. That will overwrite your data.

You can use these that do not auto mount swap.
       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

Swap is not a shared data partition, but where RAM is swapped into when you run out of RAM. Most systems now have a lot of RAM and often do not use swap. My 4GB RAM system very rarely uses any swap. 
Swap is just unformatted space that it copies RAM memory into. But if nothing has been copied you may be able to just reset partition back to NTFS.

 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

From Parted Magic or Gparted you should also have testdisk. It finds old partitions and may let you recover the partition. It may let you do deeper search and find files. If so and you do not have good copies back those up before anything else to another drive.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

