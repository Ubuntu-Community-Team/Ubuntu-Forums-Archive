---
title: "Software RAID grub boot error"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by vw16v on 2016-10-23
Hi, I was reloading my linux box from scratch last night and decided to try software RAID 0 since I have two identical 75GB drives and figured this would provide a nice boost in read/write speeds. So, during the install I noticed an option to do software RAID and choose that route. I told the software to RAID 0 my two drives. Everything went fine with the install but as soon as I rebooted I'm getting this error.

error: failure reading sector 0xb30 from 'fd0' 
error: disk 'mduuid/LONG#,1' not found.

I tried messing with some of the hard drive settings in BIOS but I can't get past this error. Any ideas how I might be able to fix this in grub or do I have to backout of software RAID 0? 

I recall the Guided Partitioning did the following after setting up my software RAID0.
RAID 0 159 GB Auto partition suggestion>
#1 Primary 159.4 GB ext4
#5 logical 534.6 MB swap
SCSI1 80G K RAID
and
SCSI2 80G K RAID

I was really excited with the idea of doing software RAID so I'm hoping to get this fixed without reloading and going back to non-RAID. Thanks for any suggestions or ideas.

---

### Post by vw16v on 2016-10-24
After spending time researching this a little more I think I might be close to a potential solution? Can anybody advise before I try to get my grub to recognive my new 16.04 xunbutu install? I downloaded systemrecovery CD and I'm currently booted in it checking my partitions,ect.I don't have the specific grub error output but it''s pretty much what I listed in my first post. Here's my drive setup and some output.

```
root@sysresccd /root % fdisk -l
Disk /dev/loop0: 353.1 MiB, 370208768 bytes, 723064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0006b327

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1  *     2048 156301311 156299264 74.5G fd Linux raid autodetect


Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0f4216be

Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1        2048 156301311 156299264 74.5G fd Linux raid autodetect


Disk /dev/md0: 149 GiB, 159916228608 bytes, 312336384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disklabel type: dos
Disk identifier: 0x992ec57a

Device     Boot     Start       End   Sectors   Size Id Type
/dev/md0p1             63 311291504 311291442 148.4G 83 Linux
/dev/md0p2      311291505 312335729   1044225 509.9M  5 Extended
/dev/md0p5      311291568 312335729   1044162 509.9M 82 Linux swap / Solaris

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 5 does not start on physical sector boundary.
root@sysresccd /root % mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Oct 23 03:39:13 2016
     Raid Level : raid0
     Array Size : 156168192 (148.93 GiB 159.92 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sun Oct 23 03:39:13 2016
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 512K

           Name : dubstud:0
           UUID : bbcb78f0:0c354275:884cd2c7:3039c061
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
root@sysresccd /root % blkid
/dev/loop0: TYPE="squashfs"
/dev/sr0: UUID="2016-10-02-07-25-26-00" LABEL="sysrcd-4.8.3" TYPE="iso9660"
/dev/sda1: UUID="bbcb78f0-0c35-4275-884c-d2c73039c061" UUID_SUB="3112c83b-2bad-54ba-d70e-df6974ee8a1b" LABEL="dubstud:0" TYPE="linux_raid_member" 

PARTUUID=                             "0f4216be-01"
/dev/md0p1: UUID="7962bf1a-43e9-4f26-988b-06646a988405" TYPE="ext4" PARTUUID="992ec57a-01"
/dev/md0p5: UUID="5e84b8ad-bb71-4fd1-b572-32002b7f367d" TYPE="swap" PARTUUID="992ec57a-05"
/dev/sdb1: UUID="bbcb78f0-0c35-4275-884c-d2c73039c061" UUID_SUB="2e32a38c-7033-9740-cfd9-3e9c3df0a9da" LABEL="dubstud:0" TYPE="linux_raid_member" 

PARTUUID=                             "0006b327-01"
/dev/md0: PTUUID="992ec57a" PTTYPE="dos"


```

What I'm thinking of trying is possibly this. 

```
su grub-install /dev/sda1 followed by update-grub

```
I was thinking that might help since /dev/sda1 is the first logical drive in my RAID0 setup. I noticed that /dev/sdb1 currently have an * next to boot in fdisk -l output indicating it's where grub is set to boot from??I don't think I should point grub to /dev/md0p1 or something else? Thanks for any suggestions!

---

### Post by vw16v on 2016-10-24
I'm hoping this might complete what's need to possibly fix my issue.  
Exact Error>
error: failure reading sector 0xb30 from 'fd0'
error: disk 'mduuid/bbcb78f0:0c354275:884cd2c7:3039c061' not found.
Enterering rescue mode...
grub rescue> _

Also I have a floppy since I'm pretty sure fd0 is the floppy so not sure what I get that error?

This is the specific drive or UUID I get the error on and it's my RAID0  id per mdadm -D /dev/md0 output.

UUID : bbcb78f0:0c354275:884cd2c7:3039c061

```
root@sysresccd /root % blkid
/dev/loop0: TYPE="squashfs"
/dev/sr0: UUID="2016-10-02-07-25-26-00" LABEL="sysrcd-4.8.3" TYPE="iso9660"
/dev/sda1: UUID="bbcb78f0-0c35-4275-884c-d2c73039c061" UUID_SUB="3112c83b-2bad-54ba-d70e-df6974ee8a1b" LABEL="dubstud:0" TYPE="linux_raid_member" 

PARTUUID=                             "0f4216be-01"
/dev/md0p1: UUID="7962bf1a-43e9-4f26-988b-06646a988405" TYPE="ext4" PARTUUID="992ec57a-01"
/dev/md0p5: UUID="5e84b8ad-bb71-4fd1-b572-32002b7f367d" TYPE="swap" PARTUUID="992ec57a-05"
/dev/sdb1: UUID="bbcb78f0-0c35-4275-884c-d2c73039c061" UUID_SUB="2e32a38c-7033-9740-cfd9-3e9c3df0a9da" LABEL="dubstud:0" TYPE="linux_raid_member" 

PARTUUID=                             "0006b327-01"
/dev/md0: PTUUID="992ec57a" PTTYPE="dos"
```

---

### Post by dosergio on 2017-01-02
I suppose grub-install should be done to a DISK (sdx) not a partition (sdx1).

/dev/sdb = disk
/dev/sdb1 = first partition

grub must reside in disk as the first mbr (master boot record) of the disk is where grub will see the full disk...

---

