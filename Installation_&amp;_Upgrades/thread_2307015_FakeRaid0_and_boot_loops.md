---
title: "FakeRaid0 and boot loops"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by LastStarDust on 2015-12-21
Hello.
I have (re)installed Ubuntu 14.04.3 on a double disk FakeRaid desktop PC.
Until now I have always used dmraid to manage the raid array and it kind of worked.
This time I decided to use mdadm because I read it is actively developed and eventually is going to replace dmraid. 
OS installation is OK. Grub2 installation is OK, but if I boot the standard way, I end up with a boot loop where
```
mdadm: create group disk not found
```
is being spammed slowly but endlessly. Anyway if I select in the grub menu the recovery boot option for the kernel and then resume the normal boot from there, all goes smooth.
Once logged into the system there is no problem whatsoever.
I have already tried a couple of tricks found in the internet with no success.

This is my rig:
Motherboard: Gygabyte GA-P55A-UD5
Chipset: Intel® P55 Express Chipset
Disks: 2x SAMSUNG HD322GJ (1AR10001) 320GB each in RAID0

This are as much info I was able to gather:

**$ sudo mdadm --detail --scan **
```
ARRAY /dev/md/imsm0 metadata=imsm UUID=XXX
ARRAY /dev/md/ZION container=/dev/md/imsm0 member=0 UUID=YYY

```

**$ cat /proc/mdstat**
```
Personalities : [raid0] [linear] [multipath] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid0 sda[1] sdb[0]
      625137664 blocks super external:/md127/0 128k chunks
      
md127 : inactive sdb[1](S) sda[0](S)
      4520 blocks super external:imsm
       
unused devices: <none>

```
**$ cat /etc/mdadm/mdadm.conf**
```
# mdadm.conf
#
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
ARRAY metadata=imsm UUID=XXX
ARRAY /dev/md/ZION container=XXX member=0 UUID=YYY


# This file was auto-generated on Sat, 19 Dec 2015 09:58:08 +0100
# by mkconf $Id$


$ ls /dev/md*
/dev/md126  /dev/md126p1  /dev/md126p5  /dev/md126p6  /dev/md126p7  /dev/md127


/dev/md:
imsm0  ZION  ZION1  ZION5  ZION6  ZION7

```
**$ sudo fdisk -l**
```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0xfa4d of partition table 5 will be corrected by w(rite)


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009e9d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       544921598  1250274815   352676609    5  Extended
/dev/sda5   ?   632610853   713485436    40437292   5c  Priam Edisk


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/md126: 640.1 GB, 640140967936 bytes
255 heads, 63 sectors/track, 77826 cylinders, total 1250275328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00009e9d


      Device Boot      Start         End      Blocks   Id  System
/dev/md126p1       544921598  1250274815   352676609    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/md126p5      1248046592  1250274815     1114112   82  Linux swap / Solaris
/dev/md126p6       701171712  1248046591   273437440   83  Linux
/dev/md126p7       544921600   701171199    78124800   83  Linux

```

Thanks in advance for the help.

---

### Post by lile001 on 2016-01-10
OK, I am sorry I can't help with your specific question - because you are doing it the hard way! RAID cards are cheap now -$20 -  just buy one, plug it in, and you are done.  (May need to configure it via bios options, YMMV)  Fuhgettabout all this mdasm stuff.  That may meet your needs and you can skip all this complexity.

---

