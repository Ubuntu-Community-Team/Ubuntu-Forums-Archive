---
title: "Upgrade trouble"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by asai on 2010-07-19
Hi,
I am helping a guy with upgrading from 9.04 to 10.04.
His problem is lack of disk space.

He gave me this from fdisk -l:
```
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5e27b1ed

Device Boot Start End Blocks Id System
/dev/sda1 1 2 16033+ de Dell Utility
/dev/sda2 * 3 6528 52420095 7 HPFS/NTFS
/dev/sda3 6529 7294 6152895 f W95 Ext'd (LBA)
/dev/sda5 6529 7294 6152863+ 7 HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12b06d90

Device Boot Start End Blocks Id System
/dev/sdb1 1 24039 193093236 7 HPFS/NTFS
/dev/sdb2 24040 24321 2265165 f W95 Ext'd (LBA)
/dev/sdb5 24040 24321 2265133+ 82 Linux swap / Solaris


```
There is XP installed also. I am a little confused with this output, though.
It doesn't look like this when i do this on my own machine.
Could this be a Wubi installation?

---

### Post by bcbc on 2010-07-19
It looks like it must be wubi as there is no ext3/4 partition. But curiously there is a swap partition. It is possible to use a swap partition with wubi (in order to hibernate), but this is unusual.

Check the /etc/fstab and you'll see / mounted on /host/ubuntu/disks/root.disk if it's wubi.

Running [bootinfoscript]("http://bootinfoscript.sourceforge.net/") will also tell you.

---

