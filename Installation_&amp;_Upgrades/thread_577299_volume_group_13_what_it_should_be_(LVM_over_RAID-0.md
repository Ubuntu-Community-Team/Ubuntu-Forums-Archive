---
title: "volume group 1/3 what it should be (LVM over RAID-0)"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by adante on 2007-10-16
EDIT: SOLVED see bottom of post
Hi,
I installed ubuntu using the guide [https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid) (alternate installer) so that I could install onto a 3x200gb RAID-0 root (yes i know, i am silly).

Setup as follows
three 200gb drives, /dev/sda, sdc, sdd

each drive partitioned like this (I show sda, sdc and sdd are identical):
```
root@pveer:/etc/lvm/backup# fdisk /dev/sda
[...]
Command (m for help): p

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7         137     1052257+  fd  Linux raid autodetect
/dev/sda3             138       24321   194257980   fd  Linux raid autodetect

```

So the idea is, I want /dev/md0 to be a 3gb swap (raid0) of /dev/sdX2, and the rest being a /dev/md1 root filesystem of raid-0'd /dev/sdX3 partitions.

unfortunately for some reason while the swap is fine, the root filesystem is one third the size that it should be (185gb, i expect it to be 555). 

So, I was thinking perhaps I mucked something up and made a RAID-1 system. But this does not appear to be the case.

```
root@pveer:/etc/lvm/backup# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Oct 16 12:45:12 2007
     Raid Level : raid0
     Array Size : 582773568 (555.78 GiB 596.76 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Oct 16 15:12:30 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 01d9683f:41f01b7f:f0e38766:535fcb1e
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       35        2      active sync   /dev/sdc3

```


however, I am a little confused as to what lvm is seeing. lvmdiskscan seems okay (note bold)

```
lvm> lvmdiskscan
  /dev/ram0    [       64.00 MB]
  /dev/md0     [        3.01 GB] LVM physical volume
  /dev/vg1/lv1 [      185.26 GB]
  /dev/ram1    [       64.00 MB]
  /dev/sda1    [       47.03 MB]
**  /dev/md1     [      555.78 GB] LVM physical volume**
  /dev/vg0/lg0 [        3.01 GB]
  /dev/ram2    [       64.00 MB]
  /dev/ram3    [       64.00 MB]
  /dev/ram4    [       64.00 MB]
  /dev/ram5    [       64.00 MB]
  /dev/ram6    [       64.00 MB]
  /dev/ram7    [       64.00 MB]
  /dev/ram8    [       64.00 MB]
  /dev/ram9    [       64.00 MB]
  /dev/ram10   [       64.00 MB]
  /dev/ram11   [       64.00 MB]
  /dev/ram12   [       64.00 MB]
  /dev/ram13   [       64.00 MB]
  /dev/ram14   [       64.00 MB]
  /dev/ram15   [       64.00 MB]
  /dev/sdb1    [       47.03 MB]
  /dev/sdc1    [       47.03 MB]
  /dev/sdd1    [      465.76 GB]
  0 disks
  22 partitions
  0 LVM physical volume whole disks
  2 LVM physical volumes

```

but vgdisplay and vgs show the volume group created from /dev/md1 to be 185

```

lvm> vgs
  VG   #PV #LV #SN Attr   VSize   VFree
  vg0    1   1   0 wz--n-   3.01G    0
[B]  vg1    1   1   0 wz--n- 185.26G    0
[/B]
lvm> vgdisplay
  --- Volume group ---
  VG Name               vg1
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
[B]  VG Size               185.26 GB
[/B]  PE Size               4.00 MB
  Total PE              47426
  Alloc PE / Size       47426 / 185.26 GB
  Free  PE / Size       0 / 0
  VG UUID               C33vja-4RJC-gBmz-FpM4-ROdG-2yGs-1eij2t

```

so what confuses me is that while the /dev/md0 (the 3gb swap raid-0) seems to be fine, the /dev/md1 is not.

For what it's worth I do get good raid like performance across both devices:

```

root@pveer:~# hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   1220 MB in  2.00 seconds = 609.25 MB/sec
 Timing buffered disk reads:  344 MB in  3.01 seconds = 114.29 MB/sec
root@pveer:~# hdparm -tT /dev/md1

/dev/md1:
 Timing cached reads:   1208 MB in  2.00 seconds = 604.19 MB/sec
 Timing buffered disk reads:  340 MB in  3.01 seconds = 112.96 MB/sec
root@pveer:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1200 MB in  2.00 seconds = 599.69 MB/sec
 Timing buffered disk reads:  126 MB in  3.01 seconds =  41.82 MB/sec

```


i am new to ubuntu and raid management but this seems wrong to me.. does anybody know what is wrong?


For completeness I include the details of the /dev/md0 device which is working fine. As far as I can tell it is basically identical to the md1 setup which confuses me more :confused:
```
root@pveer:/etc/lvm/backup# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Oct 16 12:45:05 2007
     Raid Level : raid0
     Array Size : 3156480 (3.01 GiB 3.23 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Oct 16 15:21:04 2007
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : c0dcf1bf:7fa655df:fcf8f3cd:fcbdcbe8
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2

  --- Volume group ---
  VG Name               vg0
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  2
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               3.01 GB
  PE Size               4.00 MB
  Total PE              770
  Alloc PE / Size       770 / 3.01 GB
  Free  PE / Size       0 / 0
  VG UUID               M2sEuC-PIPt-x2IR-QDtp-uob0-iQg4-hRfhVG

```


-------

this was solved by running pvresize on /dev/md1, then lvextend on the logical volume, with the number of free extents obtained from vgdisplay

---

