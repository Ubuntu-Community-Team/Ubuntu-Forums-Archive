---
title: "RAID won't mount"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by frank_daugaard2 on 2015-04-24
I have a RAID5 array with 3 WD RED disks (sdb, sdc sdd), where one drive gave up. I replaced the drive, and now the array won't mount.

My mdadm conf:
```
# mdadm.conf#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md0 UUID=76d1edff:a1188431:0cf33d4d:3ef09af2


# This file was auto-generated on Fri, 24 Apr 2015 06:49:33 +0200
# by mkconf $Id$
```

**'cat /proc/mdstat' **gives:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]md0 : active raid5 sdd[2] sdc[0] sdb[3]
      5860270080 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
```

**'fsck /dev/md0'** gives

```
fsck from util-linux 2.20.1e2fsck 1.42.9 (4-Feb-2014)
fsck.ext4: Filesystem revision too high while trying to open /dev/md0
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

**'mdadm -E /dev/sd[bcd]'** gives

```
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 76d1edff:a1188431:0cf33d4d:3ef09af2
           Name : movano:0
  Creation Time : Mon Apr  6 00:07:18 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 5860270080 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 85875e25:589122cb:689b974e:1cf4b988


    Update Time : Fri Apr 24 02:56:16 2015
       Checksum : d8b33362 - correct
         Events : 232


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
millenium@ubuntu:~$ sudo mdadm -E /dev/sd[bcd]
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 76d1edff:a1188431:0cf33d4d:3ef09af2
           Name : movano:0
  Creation Time : Mon Apr  6 00:07:18 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 5860270080 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 85875e25:589122cb:689b974e:1cf4b988


    Update Time : Fri Apr 24 02:56:16 2015
       Checksum : d8b33362 - correct
         Events : 232


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 76d1edff:a1188431:0cf33d4d:3ef09af2
           Name : movano:0
  Creation Time : Mon Apr  6 00:07:18 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 5860270080 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 9732beb4:34a4d203:a8c351d1:788be3c0


    Update Time : Fri Apr 24 02:56:16 2015
       Checksum : 5ba6b0ea - correct
         Events : 232


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 76d1edff:a1188431:0cf33d4d:3ef09af2
           Name : movano:0
  Creation Time : Mon Apr  6 00:07:18 2015
     Raid Level : raid5
   Raid Devices : 3


 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 5860270080 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 5860270080 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b2db48cc:b885a2b6:d1085a95:ecbe42a4


    Update Time : Fri Apr 24 02:56:16 2015
       Checksum : cd68b428 - correct
         Events : 232


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAA ('A' == active, '.' == missing)
```

When I try to mount the array as EXT4 (originally EXT4 before dead disk) I get this:

```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

**'dmesg | tail'** gives

```
[   85.150872] EXT4-fs (md0): Couldn't mount because of unsupported optional features (1fd00001)
```

---

