---
title: "gparted reports 'error' with otherwise fine RAID partitions"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2008-04-15
Running Ubuntu 7.10 on two identical hard-drives with md0 (root) and md1 (swap) mirrored partitions.  As far as I can tell from the command-line tools (see below) everything is fine.  But GParted reports "couldn't find valid filesystem superblock."  It also labels the array 'md0p1' for some reason?

Is it possible that Gparted just doesn't understand mdadm-created arrays?  The installed version of Gparted is 3.3 whereas the current version is 3.6, but I haven't been able to test anything newer.  The 3.4 LiveCD has some boot-up error, and the 3.6 download won't build.

Here's what mdadm etc has to say about my arrays:
```
> sudo mdadm --detail /dev/md0

/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Mar 21 18:08:41 2008
     Raid Level : raid1
     Array Size : 34178176 (32.59 GiB 35.00 GB)
  Used Dev Size : 34178176 (32.59 GiB 35.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 15 13:27:07 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9586d6d5:a0fd9909:eb18cd94:733d7b37
         Events : 0.1099

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1


> sudo mdadm --detail /dev/md1

/dev/md1:
        Version : 00.90.03
  Creation Time : Fri Mar 21 18:08:48 2008
     Raid Level : raid1
     Array Size : 4883648 (4.66 GiB 5.00 GB)
  Used Dev Size : 4883648 (4.66 GiB 5.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Apr 15 13:26:49 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5fe37d1c:35692b2e:f3679379:85fff429
         Events : 0.26

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
```
And my mdadm.conf file seems pretty simple and straightforward:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=9586d6d5:a0fd9909:eb18cd94:733d7b37
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=5fe37d1c:35692b2e:f3679379:85fff429

# This file was auto-generated on Tue, 01 Apr 2008 01:06:47 +0000
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $
```

So, is Gparted simply wrong about my array and I should ignore it?  Or is there actually something wrong?   I had previously removed one of the drives for testing, then re-added it and resynced it.  Could something have changed, i.e., the partition sizes aren't exactly as they were before?

---

### Post by bsmith1051 on 2008-04-15
hmm, another possible clue.  Fdisk reports that the re-added drive (sda) has 2 cylinders more then sdb, so sda2 is slightly larger than sdb2.  But the md1 array doesn't seem to mind....
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063489

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4255    34178256   fd  Linux raid autodetect
/dev/sda2            4256        4865     4899825   fd  Linux raid autodetect


Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00063489

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4255    34178256   fd  Linux raid autodetect
/dev/sdb2            4256        4863     4883760   fd  Linux raid autodetect
```

---

