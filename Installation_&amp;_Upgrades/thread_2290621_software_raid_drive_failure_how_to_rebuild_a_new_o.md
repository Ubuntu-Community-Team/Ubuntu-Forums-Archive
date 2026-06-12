---
title: "software raid drive failure how to rebuild a new one?"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by ulao2 on 2015-08-13
I had a friend of mine install a software raid on my linux box and one drive seems to have developed bad sectors on the raid section. When I boot I get a grey screen. If I hit escape in time I get a secondary boot options that allow me to boot with a degraded raid config. the OS comes up and works fine but I'd like to have that raid rebuilt. 

I'm guessing you need to know a bit of info but I'm not sure what so please ask and ill get what I can.
Here is fstab if that helps.

```
UUID=6064645f-2a04-4fb1-8807-89886c7ecd4d /               ext4    errors=remount-ro 0       1
UUID=8106df35-b006-4c0d-b509-9117ad3fd1f7 none            swap    sw              0       0
UUID=ff7bcec5-e199-48db-89e5-2f329f69867a none            swap    sw              0       0
```


mdstat says
```
cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0]
      55664097 blocks super 1.2 [2/1] [U_]

unused devices: <none>

```
mdadm says 
```

sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Feb 15 15:49:56 2013
     Raid Level : raid1
     Array Size : 55664097 (53.09 GiB 57.00 GB)
  Used Dev Size : 55664097 (53.09 GiB 57.00 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Thu Aug 13 18:35:22 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : sysresccd:0
           UUID : bba30334:f469b355:3db73527:c18a34ba
         Events : 2737145

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed


```


How does one allow raid to re image the new drive?

---

