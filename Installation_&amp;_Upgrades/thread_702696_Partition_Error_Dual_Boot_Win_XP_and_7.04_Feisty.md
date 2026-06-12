---
title: "Partition Error: Dual Boot Win XP and 7.04 Feisty"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Sin2800 on 2008-02-20
I am trying to Install Ubuntu 7.04 on my computer for a dual boot with Windows XP. Every time I try to resize the main XP NTFS disk to make an Unallocated Partition, (which I freed 13 GB of space ONLY for the boot files, Ubuntu D/Ls, etc. are going on my external) I get an error message: 

> run simulation    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda2 -s 66052063232 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 76133188096 bytes (76134 MB)
Current device size: 76133191680 bytes (76134 MB)
New volume size : 66052059648 bytes (66053 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61900 MB (81.3%)
Collecting resizing constraints ...
Needed relocations : 1846119 (7562 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1040 > 1024), not yet supported!
Please try to free less space.

I have tried changing the size of the new partition 3 times, but it still gives that error. I know how to partition the drive, and I have all my important files backed up on my External USB Hard Drive. I am running Gparted off the live CD to do this. I already have a  partition set up on my External for my Ubuntu data (I made it ext3, but I am still not sure what format I should use for data).

Here are my Specs: 

Dell Dimention 3000 Desktop
2 GB DDR RAM
70 GB Internal HDD
250 GB External Seagate USB HD
256 MB ATI Radeon 9250 PCI GFX Card (the reason I am not using Gutsy)
Intel Pentium 4 Processor

Any help would be very appreciated :) . Thanks!

---

### Post by zvacet on 2008-02-20
Try to defragment windows few times before you shrink it.That may help.And if you ask for Ubuntu data format partition as ext3.

---

### Post by jazzgossen on 2008-03-03
If just defragmenting doesn't help, try to remove the files hiberfil.sys and pagefile.sys from the NTFS partition, from Ubuntu. Then resize (but make sure to leave enough space on the NTFS partition so that they can be recreated by Windows the next time you boot). That worked for me.

---

