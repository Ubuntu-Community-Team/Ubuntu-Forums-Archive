---
title: "Booting from grub (hd0,4) even if I install it on (hd0,5) ?"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-11-14
I have a multi-boot. I had set it up so it boots from (hd0,5) as I am not planning to upgrade the Ubuntu on that one. So I am using its grub/menu.lst for all.

But when yesterday I did a full install 8.10 on my (hd0,4) it changed the booting grub to that partition. But even if I do a grub> root (hd0,5) and a grub> setup (hd0,5), it keeps booting from (hd0,4) any way.

How can I fix this ?

> 
I have Windows XP, Ubuntu 8.04 on sda5, Ubuntu 8.10 on sda6 and Fedora 9 on sda7. The sdb is only for storing and backups.

grub> find /sbin/init
 (hd0,4)
 (hd0,5)
 (hd0,6)

>sudo fdisk -lu

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x28842883

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20964824    10482381    7  HPFS/NTFS
/dev/sda2        20964825   160055594    69545385    f  W95 Ext'd (LBA)
/dev/sda5        20964888    62910539    20972826   83  Linux
/dev/sda6        62910603   111491099    24290248+  83  Linux
/dev/sda7       111491163   160055594    24282216   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000782bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     8385929     4192933+  82  Linux swap / Solaris
/dev/sdb2         8385930    71300490    31457280+   7  HPFS/NTFS
/dev/sdb3        71312535   176152724    52420095    b  W95 FAT32
/dev/sdb4       176152725   490223474   157035375    f  W95 Ext'd (LBA)
/dev/sdb5       176152788   226484369    25165791    7  HPFS/NTFS
/dev/sdb6       226484433   276816014    25165791   83  Linux
/dev/sdb7       276816078   329187914    26185918+  83  Linux
/dev/sdb8       433931778   486303614    26185918+  83  Linux
/dev/sdb9       486303678   490223474     1959898+   7  HPFS/NTFS
/dev/sdb10      350152803   371117564    10482381   83  Linux
/dev/sdb11      371117628   392082389    10482381   83  Linux
/dev/sdb12      392082453   413047214    10482381   83  Linux
/dev/sdb13      413047278   433931714    10442218+  83  Linux


---

### Post by meierfra. on 2008-11-14
> root (hd0,5) and a grub> setup (hd0,5), i

Do this

```
sudo grub
root (hd0,4)
setup (hd0,4)
root (hd0,5)
setup (hd0)
quit

```

This installs  the 8.10 grub to the boot sector of the the 8.10 partition and the 8.04 grub to the MBR.

also add

title Intrepid
chainloader (hd0,4)+1

to the 8.04 menu.lst.

---

### Post by Browser_ice on 2008-11-14
But since Windows is at (hd0,0) won't it messup Windows's own Grub ?

XP is on (hd0,0)
Ubuntu 8.10 on (hd0,4)
Ubuntu 8.04 on (hd0,5) => want this one to be the PC booting Grub
Fedora 9 on (hd0,6)

---

### Post by 73ckn797 on 2008-11-14
I was having boot issues after installing 8.10 64 bit on a second HD. I have 8.10 32 bit in the primary drive (hd0). 

The 64 bit was not booting from the grub menu. Upon looking into the grub menu.lst I found the entry for that drive to be incorrect. I remembered that Ubuntu uses drive UUID and inserted that info and deleted the hd* references. System now boots fine into the 64 bit drive from menu. The 32 bit boot was without issue and had not used the hd0 designation but the 64 bit did and also included the UUID. It was getting confused.

I have posted info previously about grub writing the incorrect drive info. I now know to use the UUID info.

---

### Post by meierfra. on 2008-11-14
[QUOTE=Browser_ice]But since Windows is at (hd0,0) won't it messup Windows's own Grub ?[/QUOTE]

The windows boot sector is on (hd0,0). The MBR  (which is at (hd0)) comes before that. So it does not interfere with booting Windows.

Installing the 8.04 grub to (hd0) only overwites the 8.10 grub which currently is installed at (hd0).

---

