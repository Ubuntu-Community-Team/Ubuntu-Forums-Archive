---
title: "LUKS opens but LVM lost, no LVM config backup available"
date: 2016-12-23
forum: Installation &amp; Upgrades
---

### Post by hphde on 2016-12-23
Hey,

I was recently upgrading Ubuntu from 14.04 to 16.04 and something went wrong so I did a fresh install and now I can't access the content of my backup disk any more since the backup disk LVM config is missing.

I have a 256GB SSD and a 512GB HDD in my system and use the HDD for backups and the SDD for live system and user data. The HDD was originally alone and I had Ubuntu there all with standard encryption setup. I just wiped the contents and used this disk as backup. I didn't had a clue what is really done under the hood to get this LVM/LUKS stuff going until my upgrade.

For the upgrade I removed the HDD so the installer doesn't mess with my backup. I then installed Ubuntu 16.04 by using defaults on the SDD. After reinserting the HDD the system asked my for the LUKS passphrase and that is still working. What is missing is obviously the LVM configuration. I have a backup of this ... on the encrypted disk. :( I didn't know that this required to have a working LVM ...

So I have obviously a hen and egg problem. I already made a 1:1 copy of the disk to an external USB drive so I can mess around with the live data. I tried testdisk on the decrypted disk but didn't get meaningful results. Do I have to somehow restore the LVM config before I can get to the real filesystem?

Any help is welcome.

SDD
```

~# fdisk -l /dev/sda
Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0005fbe9

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1           63    501757    501695   245M 82 Linux swap / Solaris
/dev/sda2  *    501758 976771071 976269314 465,5G  5 Extended
/dev/sda5       501760 976771071 976269312 465,5G 83 Linux
```
SDD
```

~# fdisk -l /dev/sdb
Disk /dev/sdb: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xab7c491f

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sdb1  *       2048    999423    997376  487M 83 Linux
/dev/sdb2       1001470 500117503 499116034  238G  5 Extended
/dev/sdb5       1001472 500117503 499116032  238G 83 Linux
```

mapper
```

~# ls -l /dev/dev/mapper/sda5_crypt/mapper/
total 0
crw------- 1 root root 10, 236 Dez 22 20:36 control
lrwxrwxrwx 1 root root       7 Dez 23 11:19 cryptdisk -> ../dm-3
lrwxrwxrwx 1 root root       7 Dez 22 20:36 sda5_crypt -> ../dm-0
lrwxrwxrwx 1 root root       7 Dez 22 20:36 ubuntu--vg-root -> ../dm-1
lrwxrwxrwx 1 root root       7 Dez 22 20:36 ubuntu--vg-swap_1 -> ../dm-2
```

LVM
```

~# pvdisplay 
  --- Physical volume ---
  PV Name               /dev/mapper/sda5_crypt
  VG Name               ubuntu-vg
  PV Size               238,00 GiB / not usable 3,00 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              60926
  Free PE               11
  Allocated PE          60915
  PV UUID               UIKcdK-NWq9-eqEm-bGhf-WgFW-OnX5-WyMksI
   
~# lvdisplay 
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                cJZ3qo-ubxu-dZ4B-1dhP-P5wk-ZJkM-YTid9H
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-12-21 10:42:53 +0100
  LV Status              available
  # open                 1
  LV Size                230,32 GiB
  Current LE             58961
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                IPwxH6-XFL5-jCdV-HCQ9-ggZi-lram-gxUVaq
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2016-12-21 10:42:53 +0100
  LV Status              available
  # open                 2
  LV Size                7,63 GiB
  Current LE             1954
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
~# vgdisplay 
  --- Volume group ---
  VG Name               ubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               237,99 GiB
  PE Size               4,00 MiB
  Total PE              60926
  Alloc PE / Size       60915 / 237,95 GiB
  Free  PE / Size       11 / 44,00 MiB
  VG UUID               UT0qEh-z2Ed-5JDD-GwTa-xvaE-nzOe-t4RPiQ
```

**/dev/mapper/sda5_crypt** is sda because the HDD was not present during setup

HP

---

### Post by hphde on 2017-01-09
Anyone got an idea why something like "strings" doesn't show something readable when I run into over the LUKS device? Has the LUKS/LVM setup/version/algorithm been changed between 14.04 and 16.04?

---

