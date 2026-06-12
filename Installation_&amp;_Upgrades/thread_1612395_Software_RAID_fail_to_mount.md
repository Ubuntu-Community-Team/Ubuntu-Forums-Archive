---
title: "Software RAID fail to mount"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by Rickolati on 2010-11-03
Hi all

My heart just stopped and then started beating at 200bpm

My software RAID5 seems to have failed. I have 4 2Tb drives in a RAID5 configuration. I used mdadm to assemble the drives and have been using it for a few months now.

I have the RAID array mentioned in the /etc/mdadm/mdadm.conf file as:


```
ARRAY /dev/md0 level=raid5 num-devices=4 uuid=1df999f1:4028522b:42f75c2b:ec9bbe91
```I usually mounted the drive myself after a reboot with the command:

```
sudo mount /dev/md0 /Storage
```but now this happens:

```
rick@rick-desktop:~$ sudo mount /dev/md0 /Storage/
mount: you must specify the filesystem type
rick@rick-desktop:~$ sudo mount -t /dev/md0 /Storage/
rick@rick-desktop:~$ sudo mount -t ext3 /dev/md0 /Storage/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
/proc/mdstat

```
md0 : inactive sdb[0](S) sde[3](S) sdd[2](S) sdc[1](S)
      7814057984 blocks
```
fdisk -l
```
rick@rick-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000068c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59532   478189568   83  Linux
/dev/sda2           59533       60802    10194945    5  Extended
/dev/sda5           59533       60802    10194944   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table
```It says doesn't contain valid partition but this is what it said even when stuff worked!

```
rick@rick-desktop:~$ sudo mdadm -A /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
```This seems like BAAAAD news... Please tell me this does not mean I lost two drives!! I used the drive less than 6 hours ago and since then it has been idle.

What else can I try. And if I have now lost two of the drives, how would I be able to see which two?

Regards
Richard

---

### Post by Boondoklife on 2010-11-03
It is very odd that it can not see the partition tables, even if you are using a software raid you should still have partition tables. Did you happen to make a backup of the partition tables (MBR)? If so you could try restoring it.

To backup:
```
dd if=/dev/sdX of=/tmp/sda-mbr.bin bs=512 count=1
```where X is the drive letter

To Resore:
```
dd if= sda-mbr.bin of=/dev/sdX bs=1 count=64 skip=446 seek=446
```where X is the drive letter

---

### Post by Rickolati on 2010-11-03
Thanks for the response! I have not backed the MBR up. Do you think it is worth doing a backup and restore in its current state?

I figured it was normal as each drive does not have an individual partition, but only a shared partition over the RAID drive. Was I wrong in this assumption??

I have now also done some more troubleshooting. I thought it could be due to one of the power rails from the PSU that died, so I swapped around power cables, leaving one drive off at a time. That did not make a difference, I could only get two drives up at a time(the same two).

I then figured it could be due to a dead SATA controlled. Both the dead drives are on the same SATA controller(one of two on the mobo). Does this make sense??????

Is there a way of checking if the drives have hardware failures or if the software RAID failed. I am very suspicious of both drives failing unless it is a PSU issue, but the PSU seems fine!? I would prefer not to write anything to any of the drives just yet because I am still hoping, maybe naively so, but hoping to get the drive back up and running.

Any help would be greatly appreciated!

---

### Post by Boondoklife on 2010-11-03
Ahh sorry for some reason I thought you were running a mirror! =] Yea a parity array will not show a partition table. Are both drives that are not showing up on the same sata controller? try swapping and see what happens, if the other drives are not recognizable on the same controller then I would say get another controller.

You could try spinrite, I have always had good luck with it and testing drives. As far as testing your rig, you could use a util like spinrite to stress the sata controller and drives and see if any faults occur. This would require you to have drives that you can write to, and if you are hoping for data recovery then you do not want to do this.

If you do give up on the drives I do suggest doing some testing on them to see if there is a HW fault, especially if you got the devices from the same place and same time frame. You would be surprised at how many bad batches of drives are out there and you could have fallen victim to it.

---

### Post by Doward on 2010-11-03
LMAO!

Nothing to do with my current problem (Ubuntu 10.10 not installing, just getting a blank screen / blinking cursor.  Already verified MD5 hash of the downloaded file + verify after burning) but I was not too long ago having a bear of a time getting any info about using mdadm, so I'm gonna (hopefully) throw you a line here :)

Anywho, after you do your assemble with mdadm - I recommend a simple ```
sudo mdadm --assemble --scan
``` btw run ```
sudo mdadm -D /dev/md0
``` and post back the results.

As for the 'no valid partition table' - you did the same thing I did (which is not the best idea, btw) - you created the drive with /dev/sda, /dev/sdb, etc - instead of creating linux Software RAID Partitions, and assembling with /dev/sda1, /dev/sdb1, etc.

Yes, it will work without the valid partitions - but it's not a 'best practices' setup.

Anyway, do the mdadm --detail on your mdX device after assembling and see what you have going on.

---

### Post by Boondoklife on 2010-11-03
@Doward, give the alternative CD a try. I have a laptop that will not install with anything but the alternative version.

@Rickolati, If you dont have a back up of it at this point, then there would prolly not be a point. If you get to the point where you want just get it up working and dont care about data, then you could try a mbr copy from the working drive to the other two that are not. 

NOTE: I believe this will only work if the drives are identical but if you've lost the data already it may still be worth a try.

---

### Post by Rickolati on 2010-11-03
Thanks for the response!

@Doward: I will try the suggestions and let you know. How would I go about doing the RAID so properly though? I suppose that can only be done when I'm setting up a new RAID.

I used:
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

Is there a better way? Are you saying it is should be better to create partitions on each drive and then add /dev/sdb1 /dev/sdc1 etc, so add the partitions to the RAID instead of adding the drives to the RAID?

I will try to copy the MBRs over from the good drives to the bad drives once I've given up on trying to save the data

---

### Post by Doward on 2010-11-04
> **Rickolati said:**
> Thanks for the response!

@Doward: I will try the suggestions and let you know. How would I go about doing the RAID so properly though? I suppose that can only be done when I'm setting up a new RAID.

I used:
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

Is there a better way? Are you saying it is should be better to create partitions on each drive and then add /dev/sdb1 /dev/sdc1 etc, so add the partitions to the RAID instead of adding the drives to the RAID?

I will try to copy the MBRs over from the good drives to the bad drives once I've given up on trying to save the data

That is correct.  I learned that the hard way with my own 3TB Raid 5 array.  It's ok, though - I'm setting up an 8TB Raid 5 array now, going to copy the 3TB array over, then re-set the raid array into partitions rather than whole drives.

Basically, having the raid array set up as partitions vs drives gives you a LOT more data-recovery options.

---

### Post by Rickolati on 2010-11-04
Hey man

I don't see anything mentioned about issues with using the drives rather than the partitions.

See:
[https://raid.wiki.kernel.org/index.php/Partition_Types](https://raid.wiki.kernel.org/index.php/Partition_Types)

Do you have any citation with regards to using partitions is preferable to using the drives.

Ultimately though, I want to know why the Array failed so I can avoid that in the future and I just can't seem to put my finger on it.

I have moved the faulty drives to the other SATA controller, but that did not make a difference and they still did not come up.

---

### Post by Rickolati on 2010-11-04
Also, how do I know which drive in /dev/sdX maps to which physical drive? I know which physical drives are causing trouble by unplugging one at a time, but once in the OS all the drives seem fine, /dev/sdb to /dev/sde.

How will I know which MBR to backup and which one to replace?

---

### Post by Rickolati on 2010-11-05
I found something interesting:

```
rick@rick-desktop:~$ sudo mdadm --examine /dev/sdb
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1df999f1:4028522b:42f75c2b:ec9bbe91 (local to host rick-desktop)
  Creation Time : Sun Sep  5 21:11:23 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Nov  2 23:01:00 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 44a5726e - correct
         Events : 12116

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde
rick@rick-desktop:~$ sudo mdadm --examine /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1df999f1:4028522b:42f75c2b:ec9bbe91 (local to host rick-desktop)
  Creation Time : Sun Sep  5 21:11:23 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Nov  3 11:25:14 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 44a620f2 - correct
         Events : 12124

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
rick@rick-desktop:~$ sudo mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1df999f1:4028522b:42f75c2b:ec9bbe91 (local to host rick-desktop)
  Creation Time : Sun Sep  5 21:11:23 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Nov  3 11:25:14 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 44a620e0 - correct
         Events : 12124

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
rick@rick-desktop:~$ sudo mdadm --examine /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1df999f1:4028522b:42f75c2b:ec9bbe91 (local to host rick-desktop)
  Creation Time : Sun Sep  5 21:11:23 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Tue Nov  2 23:01:00 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 44a57280 - correct
         Events : 12116

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      active sync   /dev/sde

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8       64        3      active sync   /dev/sde
```

sdb thinks all is good

sdc thinks sdd and sde is faulty

sdd thinks sdd and sde is faulty although the state of sdd is clean

sde thinks all is good

I think I will just try and mark one drive as good and see if it comes up

---

### Post by Rickolati on 2010-11-05
Wooohoooo It seems I am back up and running :)

What I did was the following:

From the examine it was clear that sdd got confused as it thought it was sdb. I figured sdc was the safer of the two "failed" drives so I did the following:

```
sudo mdadm --assemble -f /dev/md0 /dev/sdb /dev/sdc /dev/sde
```output was:

```
mdadm: forcing event count in /dev/sdb(2) from 12116 upto 12124
mdadm: forcing event count in /dev/sde(3) from 12116 upto 12124
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sdb
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sde
mdadm: /dev/md0 has been started with 3 drives (out of 4).
```I verified the integrity of a few large files I have on there and it is all good :D

```
md0 : active raid5 sdc[1] sde[3] sdb[2]
      5860543488 blocks level 5, 64k chunk, algorithm 2 [4/3] [_UUU]
```and I now have consistent --examine outputs of:

```
sudo mdadm --examine /dev/sdc[Ke
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1df999f1:4028522b:42f75c2b:ec9bbe91 (local to host rick-desktop)
  Creation Time : Sun Sep  5 21:11:23 2010
     Raid Level : raid5
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sat Nov  6 10:18:33 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 44aa0624 - correct
         Events : 12188

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      active sync   /dev/sde

   0     0       0        0        0      removed
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       16        2      active sync   /dev/sdb
   3     3       8       64        3      active sync   /dev/sde
```

I then re-added /dev/sdd

```
sudo mdadm --manage /dev/md0 --re-add /dev/sdd
mdadm: re-added /dev/sdd
```/proc/mdstat

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd[4] sdc[1] sde[3] sdb[2]
      5860543488 blocks level 5, 64k chunk, algorithm 2 [4/3] [_UUU]
      [>....................]  recovery =  0.4% (7837720/1953514496) finish=456.3min speed=71057K/sec

```I will update once this is ultimately up and running :D

---

