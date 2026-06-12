---
title: "Problem extending a Logical Volume"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by Dave In Sidney on 2012-11-05
I am running Ubuntu 12.04.1 as a headless server and am having troubles extending the Logical Volume Group I use for /home.
I initially had a single 2TB drive and tried adding a 2nd 2TB drive, but it seems that the second drive is only partially recognized as indicated by df:

Filesystem                         1K-blocks       Used  Available Use% Mounted on
/dev/sda1                           60475476    6948644   50454836  13% /
udev                                 1793400         12    1793388   1% /dev
tmpfs                                 720856       1052     719804   1% /run
none                                    5120          0       5120   0% /run/lock
none                                 1802136          0    1802136   0% /run/shm
/dev/mapper/vgServerData-HomeData 1902411892 1879712776   22699116  99% /home

lvdisplay shows:
 LV Name                /dev/vgServerData/HomeData
  VG Name                vgServerData
  LV UUID                M38qXv-qTyh-4AGM-d3vv-n3Dh-bekt-tHrKVl
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                1.80 TiB
  Current LE             471860
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
pvdsiplay shows:
  PV Name               /dev/sdb1
  VG Name               vgServerData
  PV Size               1.82 TiB / not usable 4.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               5071
  Allocated PE          471860
  PV UUID               Z49mnJ-mhP6-kEmt-98QC-ZXLF-ZkVl-zLO1CN
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               vgServerData
  PV Size               1.82 TiB / not usable 4.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               476931
  Allocated PE          0
  PV UUID               p5iU3b-Bheh-1Nbo-1mFK-SJhG-3vHU-2lfeAt
   
and vgdisplay shows:
 VG Name               vgServerData
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  14
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               3.64 TiB
  PE Size               4.00 MiB
  Total PE              953862
  Alloc PE / Size       471860 / 1.80 TiB
  Free  PE / Size       482002 / 1.84 TiB
  VG UUID               0pFaE1-VzH2-NlmA-TnEN-EU3q-SOa2-7Ra29H
   

Any and all help and suggestions gratefully appreciated!!

---

### Post by Dave In Sidney on 2012-11-08
A little more research and I discovered that I needed to do:
- lvextend
- resize2fs

---

