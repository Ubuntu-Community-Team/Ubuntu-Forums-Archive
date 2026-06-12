---
title: "JFS Partions are not recognized anymore after upgrade to 8.04"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by mlgdr on 2008-05-01
After I upgraded from 7.10 to 8.04 I have strange problems with jfs partitions. It seems that blkid does not recognize them correctly. If I look at /etc/blkid.tab or run blkid the partitions I always get

<device DEVNO="0x0807" TIME="1209486178" SEC_TYPE="msdos" LABEL="Shared Data" UUID="78FE-9702" TYPE="vfat">/dev/sda7</device>

It is a jfs partition and it can be mounted successfully.

For another jfs partition blkid gives 
<device DEVNO="0x0805" TIME="1209486178" SEC_TYPE="msdos" LABEL="eCSDaten" UUID="C4F8-67FF" TYPE="vfat">/dev/sda5</device>

but jfs_tune -l gives a device no 0x305 instead 0x805.

It seems that blkid has problems with jfs partitions.

The problem now is when I want to mount such a jfs partition at boot time. Because in /etc/fstab all partitions are references using their UUID the boot fails, because a partition with the given UUID could not be found. 

Does anybody know what I can do, that blkid knows my jfs partitions again.

---

