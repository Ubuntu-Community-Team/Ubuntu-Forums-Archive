---
title: "Triple Boot Grub vs WIN 7 Bootloader"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by alectheface on 2013-08-13
Hi All,
   OK, I have got myself in a bit of a mess im afraid. I have gone for a triple boot system. XP, Win7 and Ubuntu. Everything was OK but I shrank my XP partition to make more space for Win 7, but now I can't boot into Win7. I seem to have both WIN7 and Grub bootloaders on my computer, so please could I have a bit of help sorting out this mess!

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d5362

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81922047    40960992+   7  HPFS/NTFS/exFAT
/dev/sda2        81922048   332031999   125054976    7  HPFS/NTFS/exFAT
/dev/sda3       332032000   390625279    29296640   83  Linux
/dev/sda4       390627326   625141759   117257217    5  Extended
/dev/sda5       390627328   406249471     7811072   82  Linux swap / Solaris
/dev/sda6       406251520   625141759   109445120    b  W95 FAT32

```


I am aware of the following partitions
sda1 = xp (32bit)
sda2 = win7(64 bit)
sda3 = ubuntu (64 bit)
sda6 = Files (Fat 32, for exchangine between OS)

also sda5 = linux swap space


I would really like to get win 7 booting properly, and then remove one of the bootloaders so I only have 1. 
Thanks in advance, Alec

---

### Post by fantab on 2013-08-13
Reinstalling Grub should solve the issue for you. Use **[BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair")**. Just do the 'Recommended Repair', which Boot-Repair suggest and you should be good.

---

