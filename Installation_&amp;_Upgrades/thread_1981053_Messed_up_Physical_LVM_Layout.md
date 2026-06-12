---
title: "Messed up Physical LVM Layout"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by kodiakz on 2012-05-16
Hi there,

I have an almost fresh alternate installation of 12.04 64bit. Partition of sda:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000da95b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          393214  1953523711   976565249    5  Extended
/dev/sda5          393216  1953523711   976565248   8e  Linux LVM

```

Output of pvdisplay:

```
  Incorrect metadata area header checksum
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               sdbg
  PV Size               931.33 GiB / not usable 1.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              238419
  Free PE               0
  Allocated PE          238419
  PV UUID               iRmhBf-8wOA-0kxF-tnGD-MBjv-dj60-JTKZTm
   
  "/dev/sda1" is a new physical volume of "931.51 GiB"
  --- NEW Physical volume ---
  PV Name               /dev/sda1
  VG Name               
  PV Size               931.51 GiB
  Allocatable           NO
  PE Size               0   
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               PNF3Jh-WXTF-qgx1-YWGt-BsXB-LTuK-TN8mc2

```

Output of lvdisplay:

```
  Incorrect metadata area header checksum
  --- Logical volume ---
  LV Name                /dev/sdbg/volroot
  VG Name                sdbg
  LV UUID                QX68sf-7MPG-vktE-yhL8-zIUE-fUlb-SL7JwN
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                18.62 GiB
  Current LE             4768
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/sdbg/volrootsnap
  VG Name                sdbg
  LV UUID                4d6z02-8B47-Hm2S-ghqG-EO9v-OIP3-jv0qRi
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                18.62 GiB
  Current LE             4768
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/sdbg/volswap
  VG Name                sdbg
  LV UUID                LpmHOV-Kcmz-WhiF-zDM2-Wza5-AFQ2-JdsAuN
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                18.62 GiB
  Current LE             4768
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Name                /dev/sdbg/volhome
  VG Name                sdbg
  LV UUID                KJ1yYl-kRA9-CyZF-O0Lm-FKn7-ysae-i4e5SH
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                875.45 GiB
  Current LE             224115
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
```

Layout was strange already during installation, but I could not get rid of having two physical devices, it insisted to create two. And now it seems like the wrong one includes /boot on sda1. Any chance to get that fixed? What happens if I delete PV sda1?

---

### Post by kodiakz on 2012-05-22
I was brave enough and removed pv sda1, resolved. I had to dismount /boot before removing the pv, and updated fstab with the new UUID and just to be sure  dpkg-reconfigure grub-pc.

---

