---
title: "Problem re-sizing Raid 1 array"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by TerryT on 2011-08-09
I have a problem with my Raid 1 array. I've upgraded a 2 x 1TB setup
to a 2 x 2TB configuration by sync'ing in the new drives, one at a
time. Then I issued a

mdadm --grow /dev/md3 --size=max

to expand my /home partition to take up the new space. Everything
seemed to have worked, i.e.,

mdadm -D /dev/md3 gives 1.8 TB which is correct:

/dev/md3:
        Version : 0.90
  Creation Time : Fri Feb 12 15:05:39 2010
     Raid Level : raid1
     Array Size : 1838767680 (1753.59 GiB 1882.90 GB)
  Used Dev Size : 1838767680 (1753.59 GiB 1882.90 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Tue Aug  9 01:50:02 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 058638d9:1a1ea809:518942a9:7ff48aba
         Events : 0.1434974

    Number   Major   Minor   RaidDevice State
       0       8       20        0      active sync   /dev/sdb4
       1       8       36        1      active sync   /dev/sdc4


and fdisk -l /dev/md3 gives the same:

Disk /dev/md3: 1882.9 GB, 1882898104320 bytes
2 heads, 4 sectors/track, 459691920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

BUT, df -h gives:

/dev/md2               92G   12G   76G  14% /
none                  3.9G  776K  3.9G   1% /dev
none                  4.0G  164K  4.0G   1% /dev/shm
none                  4.0G   92K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
/dev/md0              1.4G   80M  1.3G   6% /boot
/dev/md3              810G  212G  557G  28% /home

i.e., it is reporting the original Raid 1 partition size for /home.

Any help on this would be much appreciated. The partition types are
all fd.

Thanks,
Terry

---

### Post by TerryT on 2011-08-09
Problem solved ... I had forgotten to expand the filesystem on /dev/md3 with resize2fs /dev/md3. Thanks, Terry.

---

