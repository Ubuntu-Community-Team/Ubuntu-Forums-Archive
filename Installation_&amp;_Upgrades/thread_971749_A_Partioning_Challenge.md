---
title: "A Partioning Challenge"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2008-11-05
I will be happy to provide this in 2 stages because I do not want to be accused of not providing enough information. gparted or partition editor snap shot does not render as specific condition as one taken from gparted live CD.
However (NEWBIE CHALLENGE) I cannot locate the one taken from gparted that resides /root.gparted.jpeg
So first off will someone tell me how to locate it in my file system 
or are these enough:
 sudo fdisk -lu
[sudo] password for allen: 

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99d799d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    30860864    15430401    7  HPFS/NTFS
/dev/sda3        30860865    78140159    23639647+   5  Extended
/dev/sda5        76421268    78140159      859446   82  Linux swap / Solaris
/dev/sda6        30860991    74429144    21784077   83  Linux
/dev/sda7        74429208    76421204      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System

In anticipation of that being enough how do I get gparted to delete that extended so that I can finally arrive at
sda1
sda2 Swap
sda3 8.10
This is what nautilus is saying creates best for it to work.
I have endeavored to be as clear as I could and will follow to the letter any suggestions that lead to resolution

Thanks in advance

Allen](*,)

---

