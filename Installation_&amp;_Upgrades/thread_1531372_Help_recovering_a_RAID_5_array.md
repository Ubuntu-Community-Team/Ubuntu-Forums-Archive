---
title: "Help recovering a RAID 5 array"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by shaknbak on 2010-07-14
Hello,

I'm a nube to linux and Ubuntu but have found that it is a solution to a problem I have.

I have a Buffalo Terastation NAS that started to report bad sectors. It was setup RAID 5 with 4 1 terabyte drives. I went to replace the drive and everything went down hill. The array somehow ended up being corrupt. After much research and playing around I've found I can access the folders/files of the array using Ubuntu. I pulled the drives from the NAS and attached them to my workstation and loaded Ubuntu. After loading up the drives in Ubuntu I was able to start the array and mount it. It was degraded but recovering. I could see all my files and folders. Needless to say I was thrilled until... One of the other drives reported as faulty. So I have a RAID 5 array with 2 faulty drives. Usually I would say I'm screwed and forget trying to recover my data however I know the drives are only faulty because of bad sectors and not mechanical. Also I have been able to load them up 3 times and start the copy process off onto another system. It will run for some time and then the second drives reports faulty and bam I'm back down. 

Here is my question: Is there a way I can force the array to stay up (in maybe even a read-only mode) long enough for me to capture my files? Or is there a way I can repair the drives so that all is good? Each time I have been able to get data off the drives I have to uninstall ubuntu and reinstall it and then create the array again. If I can't get the drives to stay online even in a faulty state then is there an easy way for me to tear down the array and reset the status of the drives/array and bring it back online?


Keep in mind I'm very new to the linux world. I've been messing with this for two weeks and I think it's time to ask for some help which I hate to do. In my 2 weeks if messed around with mdadm, xfs_repair, fsck, fdisk and have somewhat of an understanding of what they do however it seems like everything I run one of the tools I always end up with some sort of superblock error. I think I may have also ended up with an extra partition on each disk as well as disks belonging to multiple arrays.  but I know if I wanted to I could still get it back up long enough to get 3GB of data or so before it fails again.


Some output that may be useful.
[FONT=Times New Roman][SIZE=2]
root@ubuntu:~# fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x39b7cbe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10010    80405293+   7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          37      297171   83  Linux
/dev/sdb2              38          99      498015   83  Linux
/dev/sdb4             100      121601   975964815    5  Extended
/dev/sdb5             100         116      136521   82  Linux swap / Solaris
/dev/sdb6             117      121572   975595288+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          37      297171   83  Linux
/dev/sdc2              38          99      498015   83  Linux
/dev/sdc4             100      121601   975964815    5  Extended
/dev/sdc5             100         116      136521   82  Linux swap / Solaris
/dev/sdc6             117      121572   975595288+  83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1          37      297171   83  Linux
/dev/sdd2              38          99      498015   83  Linux
/dev/sdd4             100      121601   975964815    5  Extended
/dev/sdd5             100         116      136521   82  Linux swap / Solaris
/dev/sdd6             117      121572   975595288+  83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          37      297171   83  Linux
/dev/sde2              38          99      498015   83  Linux
/dev/sde4             100      121601   975964815    5  Extended
/dev/sde5             100         116      136521   82  Linux swap / Solaris
/dev/sde6             117      121572   975595288+  83  Linux


root@ubuntu:~# mdadm --examine /dev/sdb6
/dev/sdb6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a9a636f3:4122e808:84c227cc:8c8dc586
  Creation Time : Sun May 24 11:05:33 2009
     Raid Level : raid5
  Used Dev Size : 975595200 (930.40 GiB 999.01 GB)
     Array Size : 2926785600 (2791.20 GiB 2997.03 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Tue Jul 13 22:10:36 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 796b7307 - correct
         Events : 30706218

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       22        2      active sync   /dev/sdb6

   0     0       0        0        0      removed
   1     1       8       38        1      active sync   /dev/sdc6
   2     2       8       22        2      active sync   /dev/sdb6
   3     3       0        0        3      faulty removed
root@ubuntu:~# mdadm --examine /dev/sdc6
/dev/sdc6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a9a636f3:4122e808:84c227cc:8c8dc586
  Creation Time : Sun May 24 11:05:33 2009
     Raid Level : raid5
  Used Dev Size : 975595200 (930.40 GiB 999.01 GB)
     Array Size : 2926785600 (2791.20 GiB 2997.03 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Tue Jul 13 22:10:36 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 796b7315 - correct
         Events : 30706218

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       38        1      active sync   /dev/sdc6

   0     0       0        0        0      removed
   1     1       8       38        1      active sync   /dev/sdc6
   2     2       8       22        2      active sync   /dev/sdb6
   3     3       0        0        3      faulty removed

root@ubuntu:~# mdadm --examine /dev/sdd6
/dev/sdd6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a9a636f3:4122e808:84c227cc:8c8dc586
  Creation Time : Sun May 24 11:05:33 2009
     Raid Level : raid5
  Used Dev Size : 975595200 (930.40 GiB 999.01 GB)
     Array Size : 2926785600 (2791.20 GiB 2997.03 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Tue Jul 13 21:57:23 2010
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 796b6fc8 - correct
         Events : 30706190

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       54        4      spare   /dev/sdd6

   0     0       0        0        0      removed
   1     1       8       38        1      active sync   /dev/sdc6
   2     2       8       22        2      active sync   /dev/sdb6
   3     3       8       70        3      active sync   /dev/sde6
   4     4       8       54        4      spare   /dev/sdd6

root@ubuntu:~# mdadm --examine /dev/sde6
/dev/sde6:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : a9a636f3:4122e808:84c227cc:8c8dc586
  Creation Time : Sun May 24 11:05:33 2009
     Raid Level : raid5
  Used Dev Size : 975595200 (930.40 GiB 999.01 GB)
     Array Size : 2926785600 (2791.20 GiB 2997.03 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Tue Jul 13 21:57:23 2010
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 796b6fdc - correct
         Events : 30706190

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       70        3      active sync   /dev/sde6

   0     0       0        0        0      removed
   1     1       8       38        1      active sync   /dev/sdc6
   2     2       8       22        2      active sync   /dev/sdb6
   3     3       8       70        3      active sync   /dev/sde6
   4     4       8       54        4      spare   /dev/sdd6
[/SIZE][/FONT]

---

### Post by stlsaint on 2010-07-15
For starters i would get solid harddrives before reconstructing raid. This should get you [started]("http://www.google.com/search?hl=en&q=raid+5+recovery+in+linux&aq=f&aqi=&aql=&oq=&gs_rfai=").

---

### Post by shaknbak on 2010-07-16
I suppose I could try to assemble the array again from scratch and a new disk and see if it will resync the array on the new disk before it faults out again. Question is do I run the risk of corrupting more data if I do. If it gets me no where could I throw the drive that was bad back in and proceed coping 3GB at a time?

---

