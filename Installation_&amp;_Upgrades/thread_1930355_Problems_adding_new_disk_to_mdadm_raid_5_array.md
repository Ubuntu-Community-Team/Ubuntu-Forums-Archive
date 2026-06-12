---
title: "Problems adding new disk to mdadm raid 5 array"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by hogfan on 2012-02-23
I have been scouring the web for solution to this problem after spending over 4 hours on it last night(or this morning depending on how you look at it).  I have a healthy software RAID5 config currently using 3 Western Digital WD20EARS 2 TB drives.  The total 4 TB of usable space is now slightly more than halfway full so I am trying to add another 2 TB disk to the array and grow the array.  I had a WD20EADS 2 TB disk not being used in my other machine, so I ran all the necessary disks tests on it first and then installed it in my media server that contains the RAID5 array. I then used FDISK to create a new partition on the drive and set it for linux-raid autodetect and wrote the changes.  

Now when I try to add the new partition to the array using:

```


mdadm --add /dev/md0 /dev/sde1
```

I get a message stating that /dev/sde1 is not large enough to join the array.  

On further investigation, it appears that all drives report as 1.83 TB, but the last sector is a higher number on the WD20EARS disks than on the WD20EADS disk.  

So my question at this point is:

Is there a way to resize the partitions on the three WD20EARS drives to match (or be slightly lower than) that of the WD20EADS drive without rebuilding the entire array from scratch and losing all data on it?

This has been a very inconvenient, time-consuming, and frustrating issue.  Any suggestions to get this drive into the array are much appreciated.  I'm at witts end now.  I did not think adding an additional 2 TB drive to the array would be this difficult.

-hogfan

---

### Post by hogfan on 2012-02-24
No responses still?  Is there a more appropriate place to post this?  I know somebody has to have had this problem before with a raid 5 array on ubuntu.

-hogfan

---

### Post by hogfan on 2012-02-24
Here is some additional info:

OS: Ubuntu Server Maverick


The HDDS:

```


user@MEDIASERVER:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD writer
       product: DVD_RW ND-3540A
       vendor: _NEC
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.03
       serial: [_NEC    DVD_RW ND-3540A 1.0305091500
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: ST3250823A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/sde
       version: 3.03
       serial: 5ND0HF8V
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00091d0a
  *-disk:0
       description: ATA Disk
       product: WDC WD20EARS-00S
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 80.0
       serial: WD-WCAVY5637086
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cf6986f9
  *-disk:1
       description: ATA Disk
       product: WDC WD20EARS-00S
       vendor: Western Digital
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 80.0
       serial: WD-WCAVY5659143
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5f31d0d7
  *-disk:2
       description: ATA Disk
       product: WDC WD20EARS-00S
       vendor: Western Digital
       physical id: 2
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 80.0
       serial: WD-WCAVY5637075
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=4b7ff64f
  *-disk:3
       description: ATA Disk
       product: WDC WD20EADS-00S
       vendor: Western Digital
       physical id: 3
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
       version: 01.0
       serial: WD-WCAVY1294371
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c7c1b

```

Here is the displayed partition for the new drive from fdisk:

```
user@MEDIASERVER:~$ sudo fdisk /dev/sdd

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
81 heads, 63 sectors/track, 765633 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7c1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1          765634      765634          32   fd  Linux raid autodetect

```

And here is a displayed partiton from one of the drives already in the array (WD20EARS):
```

user@MEDIASERVER:~$ sudo fdisk /dev/sdc

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4b7ff64f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514552   fd  Linux raid autodetect

```

So as you can see the WDEARS20 drives already in the array have more blocks than the new WD20EADS drive does, although they are both 2 TB in size.  I really do not want to spend $140 on another WD20EARS drive when the drive I have (WD20EADS) is a perfectly good 2 TB HDD.  This issue was never mentioned in any of the setup guides I used when I setup my RAID5 with mdadm.  So I guess a HDD manufacturer can just pick whatever drive geometry they want to use and make it different for every model drive they make and unless the new drive has more blocks than the old drive you are just SOL at restoring your array.  Luckily I am just trying to grow my space and don't have a failed drive in the array, so I am still up and running.  I will provide any requested information if somebody with some knowledge of this can assist with resolution or workaround.  Thanks for taking the time to read.

-hogfan

---

### Post by MAFoElffen on 2012-02-24
It "is" the same size, even though the head count is different.  Did you prep your new drive with a partition?  If not, use "blkid" to check the partition size in your other drives, make it the same size as your other drives. That's what I do, partition, format ext4...

I know that you are trying to add your disk to your existing array as a hot spare, extend the size of your array (add your disk into the array), umount the array, extend the filesytem.  

Here is a page I use as reference for that:
[http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array](http://zackreed.me/articles/48-adding-an-extra-disk-to-an-mdadm-array)

---

### Post by hogfan on 2012-02-24
I did use fdisk to prep the drive and created the partition /dev/sde1.  Then I ran:
```

sudo mkfs.ext4 /dev/sde1
```

to format the partition as ext4.

When I try to add the partition to the array I get this:

```

user@MEDIASERVER:~$ sudo mdadm --add /dev/md0 /dev/sde1
mdadm: /dev/sde1 not large enough to join array
```

I think the problem may be this:

Here is the partition info for the new disk:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

```

And here is the partition info for an existing drive in the array:

```

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514552   fd  Linux raid autodetect
```

So as you can see, the new drive ends on 243201, but the existing drives in the array end on 243202.  If I try to set the END for the new drive to 243202 when creating the partition in fdisk I get an "out of range" error.

-hogfan

---

### Post by darkod on 2012-02-24
Try with cfdisk. It's similar, but more "graphical". I find it easier for quick partition making.

First make the new partition to take the whole disk, don't enter End value manually (I think you can do that with cfdisk). Then see if the End cylinder matches the other disks.

If it doesn't, try with manual value.

---

### Post by MAFoElffen on 2012-02-24
> **darkod said:**
> Try with cfdisk. It's similar, but more "graphical". I find it easier for quick partition making.

First make the new partition to take the whole disk, don't enter End value manually (I think you can do that with cfdisk). Then see if the End cylinder matches the other disks.

If it doesn't, try with manual value.
+1

Here is a quote from Ubuntu's FDISK Man Page:
> [B]
BUGS[/B][FONT=monospace]

[/FONT]There  are  several  *fdisk programs around.  Each has its problems and        strengths.  Try them in the  order  **cfdisk**,  **fdisk**,  **sfdisk**.   (Indeed,        **cfdisk**  is  a  beautiful  program  that  has strict requirements on the        partition tables  it  accepts,  and  produces  high  quality  partition        tables.   Use  it if you can.  **fdisk** is a buggy program that does fuzzy        things - usually it happens to produce reasonable results.  Its  single        advantage  is  that  it  has some support for BSD disk labels and other        non-DOS partition tables.  Avoid it if you can.  **sfdisk** is for  hackers        only  --  the  user  interface is terrible, but it is more correct than        fdisk and more powerful than both fdisk and cfdisk.  Moreover,  it  can        be used noninteractively.)         

These  days  there  also is **parted**.  The cfdisk interface is nicer, but        parted does much more: it not only resizes  partitions,  but  also  the        filesystems that live in them. Me, I used GParted and cfdisk.  If I need finer tuned and absolute settings than Gparted, then I use cfdisk.  I bounce between the 2.  If I use GParted for something that needs something closer, I turn off the option that rounds off to a cylinder.... But, I agree, cfdisk looks like a fit for you with this.

Problem it looks like it there is the same size, but differences in head, cylinders, units. Math-wise it can come out the same... but if not set manually, most disk utilities go by cylinders, which here seems to make a difference.

My curiousity is this:
```
[FONT=monospace]
[/FONT]Device Boot __ Start ____  End ____ Blocks _ Id __ System 
/dev/sdd1 ____ [COLOR=Red]765634[/COLOR] ___  765634 _ 32 ____  fd __ Linux raid autodetect

```??? The start is the same as the end? Shouldn't that start be somewhere between 1-4 with the end being as 765634 or so? Your other drives start at 1....

---

### Post by hogfan on 2012-02-24
Well it looks like fdisk is what has caused the problem.  I wish I would have known about cfdisk when I initially created the array.  When I try to display the other disks in the array in cfdisk, I get a fatal error message that says "Primary partition table is not valid.   Partition ends in the last partial cylinder of the disk".   Maybe they have fixed this problem in fdisk since I created the array and now it won't let me do the same for the new disk.  Any suggestions on how I can force the # for the end sector?  Maybe in gparted?

-hogfan

---

### Post by darkod on 2012-02-24
Not only that, what about this. The End cylinder is higher than the total???? This could be your issue. If your three disks have the same, how did they ever manage to have a partition that spans a cylinder outside the total number of cylinders???

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, [COLOR=Red]243201 cylinders
[/COLOR] Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x4b7ff64f
     Device Boot      Start         End      Blocks   Id  System
 /dev/sdc1               1      [COLOR=Red]243202[/COLOR]  1953514552   fd  Linux raid autodetect

EDIT: We were writing at the same time. I just noticed the same. You seem in trouble, as far as adding new disks is concerned. Your array works, but the partitions seem to "go outside the disk". Not sure what you can do without deleting the array and the data on it.

---

### Post by hogfan on 2012-02-24
Well I just tried sfdisk as well and tried specifying the disk size to the same as the other drives in the array, and that won't let me do it either, says it exceeds the maximum allowable size.  It's looking like I may have rebuild the entire array if I ever want to add anything to it. 

-hogfan

---

### Post by darkod on 2012-02-24
Well, it's a lot of work, but now that you know this, before you continue adding more and more data, think about this:
You said the 4TB array is about half way full, which is approx 2TB.
You have a new 2TB disk.

Create a new partition with cfdisk on the new disk, make sure the partition is correct with Start/End cylinders, copy all data it can take. If any data is left over, copy it on a smaller hdd, it wouldn't be much left over.

Destroy your array, and with cfdisk create the partition on your three disks. Make sure the partitions are correct with  Start/End cylinders too. Build a new array. Copy data back.
Add new disk to the array.

But that's lots of work man. Anyway, think about it because the more and more data you have, this operation will be more and more difficult.

---

### Post by hogfan on 2012-02-24
Thanks for all of the help.  Had to be an fdisk bug.  I don't know how it ever let me set it up that way.  I am backing up the data now and will rebuild the array, formatting with cfdisk this time.   Better to fix it now before more data is added.

-hogfan

---

### Post by hogfan on 2012-02-28
Ok, I backed everything up and got the array all rebuilt, data copied back over, added the 4th disk and grew the array.

Now I have this problem though:

I was following a couple different guides for setting up the array and made a very easy to do, but problematic mistake.  

I formatted all 3 WD20EARS drives starting at sector 2048 since they are advanced format drives.

However, when I built the array initially,  I added sdb, sdc, & sdd to the array rather than sdb1, sdc1, sdd1! When I added the fourth disk, I actually added it to the array as sde1, correctly.  So now I have a good array with 3 entire disks added and one partition. Normally I don't think is would be bad, but since these are advanced format drives and the partitions on them are set to start at 2048 because of the 4k sector size, I think the first 3 entire disks added to the array will cause raid performance problem.  

Sooo......my question is can I do the following.

1.) Fail each of the WD20EARS drives in the array, one at a time, zero the superblock on the "failed" drive, recreate the partition on the drive, starting at 2048 and then replace the "failed" drive with the newly formatted disk, adding it back into the array as (ie. sdb1 rather than sdb)?  Obviously, I would do this one disk at a time, allowing the array to rebuild after each of the 3 disks.

Or, will have to back everything up externally again and rebuild the entire array from scratch?  This is kind of a problem now because I do not have that 4th 2TB drive available to backup the data on the raid.  I do have an off-site backup of the data however, but it would take much longer for me to get that data back over to the array after it is rebuilt.   Thanks for any input on this.

-hogfan

---

