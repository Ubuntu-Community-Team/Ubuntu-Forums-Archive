---
title: "adding existing RAID1 - 16.04 Problems"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by albtross on 2016-08-20
Hi,

Before I upgraded to 16.04 my RAID1 "seemed" fine (3 years+). After the upgrade my existing RAID1 didn't automatically mount.
Now I have a problem trying to add an existing RAID1 (2 HDD 2 TB) to Ubuntu 16.04 ...I have being googling for hours and looking at instructions and I seem to have got myself more confused. As a result I am hoping someone can help.
I am very nervous as it has years of family photoes on it. and don't want to loose the data.

I seem to have run in to different errors.. where I then try to investigate and I don't know if I have broken something.... anyway, I am hoping someone can help.

Here is some outputs of some instructions I have gleaned from my searches, which i hope will shed some light on my problem and hope you can tell what I need to do (without loosing the data).

I have primary SDD drive  which I boot off, then another 2 Tb drive, plus the RAID1 (2 HDD 2 TB) which i use for storage, I don't boot off it) 

(command - sudo fdisk -l output below)

**SDD = /dev/sda (64Gb)**
Disk /dev/sda: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7081b1c5

Device     Boot    Start       End   Sectors  Size Id Type
/dev/sda1  *        2048    976895    974848  476M 83 Linux
/dev/sda2         978942 125044735 124065794 59.2G  5 Extended
/dev/sda5         978944  20977663  19998720  9.5G 83 Linux
/dev/sda6       20979712  40978431  19998720  9.5G 83 Linux
/dev/sda7       40980480  88979455  47998976 22.9G 82 Linux swap / Solaris
/dev/sda8       88981504 125044735  36063232 17.2G 83 Linux

**Second HDD = /dev/sdb (2Tb)**
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000a5341

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdb1  *            63 2047998329 2047998267 976.6G  c W95 FAT32 (LBA)
/dev/sdb2       3290992640 3907029167  616036528 293.8G 83 Linux
/dev/sdb3       2336252625 2824532234  488279610 232.8G 83 Linux
/dev/sdb4       2824532235 3290992639  466460405 222.4G 83 Linux

Partition table entries are not in disk order.

**Then the RAID Drives: /dev/sdc & /dev/sdd  = (2 x 2 TB) **
Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x2098f43b

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1        2048 3907029167 3907027120  1.8T fd Linux RAID autodetect


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


**Observation:** I noticed that the second drive /dev/sdd hasn't indicated it is **"Linux RAID autodetect"**


Command [B]sudo mdadm -E /dev/sdc
[/B]
/dev/sdc:
          Magic : Intel Raid ISM Cfg Sig.
        Version : 1.1.00
    Orig Family : bfc2033c
         Family : bfc2033c
     Generation : 00000516
     Attributes : All supported
           UUID : 9a59843e:ff97fe29:ebdb84ab:01ef7a3a
       Checksum : d68fedbc correct
    MPB Sectors : 2
          Disks : 2
   RAID Devices : 1

  Disk00 Serial : Z340KNGX
          State : active
             Id : 00040000
    Usable Size : 3907023112 (1863.01 GiB 2000.40 GB)

[RAID]:
           UUID : cf403379:8f842f08:524bd0fd:7d8ac45e
     RAID Level : 1 <-- 1
        Members : 2 <-- 2
          [B]Slots : [UU] <-- [U_]
    Failed disk : 1[/B]
      This Slot : 0
     Array Size : 3907022848 (1863.01 GiB 2000.40 GB)
   Per Dev Size : 3907023112 (1863.01 GiB 2000.40 GB)
  Sector Offset : 0
    Num Stripes : 15261808
     Chunk Size : 64 KiB <-- 64 KiB
       Reserved : 0
  [B]Migrate State : rebuild
      Map State : normal <-- degraded[/B]
     Checkpoint : 0 (512)
    Dirty State : clean

  Disk01 Serial : Z340KNJR
          State : active
             Id : 00050000
    Usable Size : 3907023112 (1863.01 GiB 2000.40 GB)

**Observation:**
I noticed that this command indicated the **failed disk 1** and "**rebuild** and **degraded**

Does it mean this disk is broken or the other disk in the RAID or something else

Command **sudo mdadm -E /dev/sdd**
dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6b1b3c7b:446a0cb2:f6df1db7:9bfda1e2
           Name : desktop:0
  Creation Time : Fri Nov 15 11:59:09 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 3906764976 (1862.89 GiB 2000.26 GB)
     Array Size : 1953382336 (1862.89 GiB 2000.26 GB)
  Used Dev Size : 3906764672 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=2352 sectors
          State : active
    Device UUID : 7f2bed73:ddba26f0:d19bea47:9376da14

    Update Time : Thu Aug 11 23:07:59 2016
       Checksum : 52a16cc1 - correct
         **Events : 428**


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

**Observation:** don't know why the output from this drive not as detailed or what is Events: 428 mean ?

**cat /proc/mdstat **
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd[0](S)
      1953382488 blocks super 1.2
       
md127 : inactive sdc[0](S)
      3028 blocks super external:imsm
       
unused devices: <none>


Please let me know is if there is more information i can provide to help.
Thanks

---

