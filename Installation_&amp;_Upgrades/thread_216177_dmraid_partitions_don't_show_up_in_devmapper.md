---
title: "dmraid partitions don't show up in /dev/mapper"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by Charles Hand on 2006-07-15
I want to dual-boot with XP on my Sony VGN-AR170P. So I boot the Ubuntu install disk, install dmraid, and I get
/dev/mapper/isw_bbcgeeehdj_Volume\ 0

Having previously shrunk the NTFS partition with Partition Magic, I use fdisk to create a boot partition, a swap partition and a FAT32 partition. Afterwards (and after rebooting and re-installing dmraid), all I see in mapper is isw_bbcgeeehdj_Volume\ 0.

fdisk, parted and cfdisk all show the partitions I created, but there are no corresponding entries in mapper for the partitions, only for the raw disk. I'm expecting to see:
isw_bbcgeeehdj_Volume\ 0
isw_bbcgeeehdj_Volume\ 01
isw_bbcgeeehdj_Volume\ 02
etc.

-Charlie

---

### Post by Charles Hand on 2006-07-20
I discovered that linux didn't like the space in the raid name. I suspected that earlier, and tried changing the name to remove the space, to no avail. But when I go back and boot XP, and use the Matrix Configurator tool, and remove the space from the name there, then reboot Linux, Linux expands out the partitions under /dev/mapper.

---

### Post by specter9mm on 2008-07-18
I am having the same problem, but there is no space in my array name.  I have gone through the process of installing dmraid on the live cd several times, and every time, I can partition my raid drive, but the partitions do not appear in /dev/mapper/.  Even after rebooting.  I am trying to do this on the 8.04.

---

