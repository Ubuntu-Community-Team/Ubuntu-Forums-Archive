---
title: "Why raid10 doesn't perform any faster than single volume?"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by forceoflight on 2011-07-28
I have a fresh m1.large Ubuntu 11.04 instance from Amazon. I read from following page that you can achieve better performance by using raid10.

[http://www.mysqlperformanceblog.com/2009/08/06/ec2ebs-single-and-raid-volumes-io-bencmark/](http://www.mysqlperformanceblog.com/2009/08/06/ec2ebs-single-and-raid-volumes-io-bencmark/)

Also MongoDB propose same approach. We are using MongoDB as a DBMS.

[http://www.mongodb.org/display/DOCS/Amazon+EC2](http://www.mongodb.org/display/DOCS/Amazon+EC2)

For some reason raid10 setup doesn't perform as well as it should against single ebs volume. There is same problem with raid1. What could cause this? I use sysbench for testing io performance. mysqlperformanceblog uses same tool.

I have used following commands when created raid10 volume:

  ```
   sudo mdadm --create /dev/md0 --chunk=256 --level 10 --raid-devices 4 /dev/xvdf /dev/xvde /dev/xvdg /dev/xvdh
     sudo mkfs.ext4 /dev/md0
     sudo mount -t ext4 -o /dev/md0 /raid10
```

I have also tested following. This seems to perform better, but it still slower than it should against single volume. I don't know why. Do you know?

   ```
 sudo mdadm --create /dev/md0 --chunk=256 --level=raid1 --raid-devices 2 /dev/xvdf /dev/xvde
    sudo mdadm --create /dev/md1 --chunk=256 --level=raid1 --raid-devices 2 /dev/xvdg /dev/xvdh
    sudo mdadm --create /dev/md2 --chunk=256 --level=raid0 --raid-devices 2 /dev/md0 /dev/md1
```

...And for single ebs I did:

    ```
mke2fs -F -j /dev/xvdi
    sudo mount -t ext4 /dev/xvdi /ebs
```

**Bench result**

**sysbench-size-256M-mode-seqwr-threads-4**

   single ebs
    Read 0b  Written 256Mb  Total transferred 256Mb  (11.253Mb/sec)
    720.20 Requests/sec executed
    
    raid10
    Read 0b  Written 256Mb  Total transferred 256Mb  (8.7705Mb/sec)
    561.31 Requests/sec executed


**sysbench-size-256M-mode-seqrd-threads-4**

    single ebs
    Read 256Mb  Written 0b  Total transferred 256Mb  (39.449Mb/sec)
    2524.72 Requests/sec executed

    raid10
    Read 256Mb  Written 0b  Total transferred 256Mb  (44.115Mb/sec)
    2823.38 Requests/sec executed

**sysbench-size-256M-mode-rndrw-threads-4**

    single ebs
    Operations performed:  41227 Read, 27487 Write, 0 Other = 68714 Total
    Read 644.17Mb  Written 429.48Mb  Total transferred 1.0485Gb  (17.893Mb/sec)
    1145.15 Requests/sec executed

    raid10
    Operations performed:  38231 Read, 25491 Write, 0 Other = 63722 Total
    Read 597.36Mb  Written 398.3Mb  Total transferred 995.66Mb  (16.593Mb/sec)
    1061.94 Requests/sec executed


**sysbench-size-256M-mode-rndwr-threads-4**

    single ebs
    Operations performed:  0 Read, 46746 Write, 0 Other = 46746 Total
    Read 0b  Written 730.41Mb  Total transferred 730.41Mb  (12.172Mb/sec)
    779.02 Requests/sec executed

    raid10
    Operations performed:  0 Read, 30435 Write, 0 Other = 30435 Total
    Read 0b  Written 475.55Mb  Total transferred 475.55Mb  (7.9251Mb/sec)
    507.21 Requests/sec executed

**sysbench-size-256M-mode-rndrd-threads-4**

    single ebs
    Operations performed:  217097 Read, 0 Write, 0 Other = 217097 Total
    Read 3.3126Gb  Written 0b  Total transferred 3.3126Gb  (56.535Mb/sec)
    3618.22 Requests/sec executed

    raid10
    Operations performed:  245950 Read, 0 Write, 0 Other = 245950 Total
    Read 3.7529Gb  Written 0b  Total transferred 3.7529Gb  (64.048Mb/sec)
    4099.09 Requests/sec executed

---

### Post by punkybouy on 2011-07-28
Your cloud storage is virtual.  It's a chunk of a Volume or LUN somewhere that appears to you as a real disk but is instead virtual.  There is no guarantee that the other "drive" is on the same chassis as the first drive and could be on the other side of the data center on slower or faster storage.  I don't think anyone recommends trying to RAID storage that is already in a RAID state.  Your single virtual disk probably sits on a volume that is already at least a RAID 5 disk and possibly RAID 6.  Heck, they can even move it around in the back ground from frame to frame depending on their needs and you would not even notice.
Typically it is not recommended to put data bases on virtual storage.  If you need fast disk for a database you should be looking at SAN fibre attached storage and not storage you access over the Internet.
It is also possible that both your virtual "disks" are on the same RAID 5 or 6 volume so there is no benefit to trying to setup a RAID 10 volume. Indeed, it could even slow you down.

---

