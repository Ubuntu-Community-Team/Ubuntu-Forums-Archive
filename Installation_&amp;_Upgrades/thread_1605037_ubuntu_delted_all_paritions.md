---
title: "ubuntu delted all paritions"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by lego12 on 2010-10-24
i specifically told ubuntu to install alongside my operation system (windows) and instead it installed over windows and deleted all the other partitions... i had 200gb of data that i completely lost
is there anyway to recover this data? because i had none of it backed up

---

### Post by sikander3786 on 2010-10-24
Sorry to hear that.

To make sure which partitions you lost, please post the output of

```
sudo fdisk -l
```

It will be too hard to do it I suspect. Give Testdisk a try.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntuforums.org/showthread.php?t=387922](http://ubuntuforums.org/showthread.php?t=387922)

It is advised that you stop using the messed up HDD. Don't save anything on that or you might be overwriting your data (if any) and that might worsen the situation.

---

### Post by lego12 on 2010-10-24
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c78d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76347   613250048   83  Linux
/dev/sda2           76347       77826    11879425    5  Extended
/dev/sda5           76347       77826    11879424   82  Linux swap / Solaris

---

### Post by sikander3786 on 2010-10-24
> **lego12 said:**
> Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003c78d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       76347   613250048   83  Linux
/dev/sda2           76347       77826    11879425    5  Extended
/dev/sda5           76347       77826    11879424   82  Linux swap / Solaris
Yeah, it is taking up all the disk space.

Go through the links posted above. I wish and hope you succeed in saving your data :-)

---

### Post by lego12 on 2010-10-24
in Testdisk most of the folders i had are empty, but system volume information was there and it had about 67 gb of random files

---

