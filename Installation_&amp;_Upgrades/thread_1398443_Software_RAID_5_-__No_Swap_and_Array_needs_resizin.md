---
title: "Software RAID 5 -  No Swap and Array needs resizing"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by n0nc3ntz on 2010-02-04
Good Afternoon to you all...

FYI.. I am very new to linux. I am trying to configure a ubuntu server 9.04 but I am having trouble figuring out RAID 5. I have a test box that I am currently working on with two Hardrives of varying sizes(on purpose). I used this tutorial regarding raid 5 and it seemed to work pretty well  -> 

[http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

Everything seemed to work ok minus a few bumps but at no point did I find any guidance on how to install my OS after RAID was configured. So I simply used this guide as reference for installing the server OS over my raid 

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

During this process I tried to add swap space but I was afraid to partition anymore space because the install alerted me that my array would be erased. So I finished my install of the OS but when I look at my disk space I have about 120GB our of 650 available. GParted tells me that both my HD are in a RAID and they both show the same available space. Here is some of my output.

fdisk -l
```

noncentz@orion:~$ sudo fdisk -l 
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe7a94361 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       60801   488384001   fd  Linux raid autodetect 
 
Disk /dev/sdb: 120.0 GB, 120034123776 bytes 
255 heads, 63 sectors/track, 14593 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe2a4e2a4 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       14593   117218241   fd  Linux raid autodetect 
 
Disk /dev/md0: 120.0 GB, 120031412224 bytes 
2 heads, 4 sectors/track, 29304544 cylinders 
Units = cylinders of 8 * 512 = 4096 bytes 
Disk identifier: 0x00000000 
 
Disk /dev/md0 doesn't contain a valid partition table 
```

mdadm -D /dev/md0

```
noncentz@orion:~$ sudo mdadm -D /dev/md0 
/dev/md0: 
        Version : 00.90 
  Creation Time : Wed Feb  3 13:54:36 2010 
     Raid Level : raid5 
     Array Size : 117218176 (111.79 GiB 120.03 GB) 
  Used Dev Size : 117218176 (111.79 GiB 120.03 GB) 
   Raid Devices : 2 
  Total Devices : 2 
Preferred Minor : 0 
    Persistence : Superblock is persistent 
 
    Update Time : Thu Feb  4 11:46:04 2010 
          State : clean 
 Active Devices : 2 
Working Devices : 2 
 Failed Devices : 0 
  Spare Devices : 0 
 
         Layout : left-symmetric 
     Chunk Size : 64K 
 
           UUID : 9139b21a:fdf498b8:e368bf24:bd0fce41 
         Events : 0.12 
 
    Number   Major   Minor   RaidDevice State 
       0       8        1        0      active sync   /dev/sda1 
       1       8       17        1      active sync   /dev/sdb1 
```

I planned on adding my swap space after I had a complete RAID but now I am lost on how I should go about adding it.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Any thoughts on how to resize my array and adding swap as well as ... well basically any help at all would be greatly appreciated. 

N0ncn3tz

---

### Post by altonbr on 2011-05-30
I'm going through the same problem as you. What did you figure out as a solution? The installer won't allow me to create a swap partition.

---

