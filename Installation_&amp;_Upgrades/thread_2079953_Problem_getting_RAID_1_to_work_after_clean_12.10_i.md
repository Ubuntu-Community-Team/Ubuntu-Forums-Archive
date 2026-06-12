---
title: "Problem getting RAID 1 to work after clean 12.10 install"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by dennmans on 2012-11-02
Hey,

I have been losing quite a bit of sleep after a botched upgrade to 12.04.  I gave up the upgrade and chose a clean install of 12.10.  That went fairly well (apart from my nvidia card problems) however I have not been able to get my RAID array to work.  

I have tried many things up until now but I have not been able to mount the array.  The OS is on a single, seperate hdd with two disks in a RAID 1 set up in Ubuntu.  

my mdstat:

```
mo@Allah:~$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[0] sdc1[1]
      976628736 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

my mdadm.conf (now, after a lot of different versions)
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

DEVICE /dev/sdb1 /dev/sdc1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=f90801d1:254147f9:feb527b3:04e7667d

# This file was auto-generated on Fri, 02 Nov 2012 11:15:00 +0100
# by mkconf $Id$
```

I have tried making and reassembling the array, which had varied results, often the array would appear at /dev/md127, a link to dev/md/Allah:0 (Allah is the hostname here).  My current configuration does show the array at /dev/md0 but I cannot mount it.
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
(I specified the format with -t)
The above configuration shows an array at /dev/md0:
```
mo@Allah:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Nov  2 12:17:58 2012
     Raid Level : raid1
     Array Size : 976628736 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976628736 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sat Nov  3 00:47:27 2012
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : Allah:0  (local to host Allah)
           UUID : f90801d1:254147f9:feb527b3:04e7667d
         Events : 17

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

```

I do not yet have an fstab entry for the array - doesn't seem much point if it isn't mounting by hand.  I am making a new post because I have already tried everything that is suggested posts on older releases and it appears a few things have changed in mdadm that might be relevant.

---

### Post by tokyobadger on 2012-11-02
What file system did you format /dev/md0 as?

---

### Post by dennmans on 2012-11-04
The filesystem is ext4, if I remember correctly.  Either ext 3 or ext 4, both of which I tried with mount -t ext3 /dev/md0 /media/mountpoint.  I reassembled md0 after the reinstall but did not specify a format.

---

### Post by dennmans on 2012-11-05
On with my experiments.  I tried:

```
/dev$ sudo fsck /dev/md0
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

doing:

```
sudo dumpe2fs /dev/md0 | grep -i superblock
dumpe2fs 1.42.5 (29-Jul-2012)
dumpe2fs: Bad magic number in super-block while trying to open /dev/md0
Couldn't find valid filesystem superblock.
```

shows that there is something wrong with my superblocks.  I am very open to suggestions at this point :-)

---

### Post by dennmans on 2012-11-06
I am now going to revert to ubuntu 12.04 with a clean install to try and solve some other issues like my nvidia card settings - I will update this post if anything interesting happens to my still broken RAID.

---

