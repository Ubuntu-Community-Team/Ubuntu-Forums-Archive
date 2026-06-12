---
title: "the attempt to mount a file system type vfat in /dev/nvme0n1p1 at boot/efi failed you"
date: 2023-03-07
forum: Installation &amp; Upgrades
---

### Post by thiagopires00 on 2023-03-07
I keep getting this error trying to instal ubuntu on my external ssd drive on my imac:
the attempt to mount a file system type vfat in /dev/nvme0n1p1 at boot/efi failed you may resume partitioning from menu

It happens after I chose the partition and click install:

My ssd is on exfat, I created a 5gb partition for the root,
Done a few times now and still nothing , anyone had the same issue

---

### Post by MAFoElffen on 2023-03-08
Linux will not boot off an exfat root. And you said you gave it a 5GB partition for root... That is not enough unless you are booting a cloud image.

Lets see what your system sees from Linux... From a terminal session booted from a LiveCD USB:
```

sudo fdisk -l | grep '^/dev/' | grep -v 'snap\|loop'
lsblk -T -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINTS | grep -v 'loop'

```

---

### Post by yancek on 2023-03-08
5GB is far to small a partition on which to install Ubuntu.  Recommend 20GB or more but at a minimum 10GB.

---

