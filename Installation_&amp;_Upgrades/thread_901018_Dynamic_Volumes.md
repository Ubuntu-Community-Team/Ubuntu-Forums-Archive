---
title: "Dynamic Volumes"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by ubyte on 2008-08-26
I know that ubuntu can read and write to dynamic volumes/partitions. I know because I have a drive that it can read about 3 of my 6 partitions. 

I am going to explain it in as few words as possible (as I have rewritten this post 2 or 3 times). The 3 drives that I can read I didn't extended (added more space) at any time while using windows. The other 3 that I can't access are the ones I later found that I needed more space and just extended the drive while using windows. 

My question is has anyone ran into this problem or am I the only one?

New to Ubuntu.
uByTe

---

### Post by cariboo on 2008-08-26
please post the output of:

```
sudo fdisk -l
```

I'm sure If we see the layout of your partitions we can probably help you.

Jim

---

### Post by ubyte on 2008-08-27
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18888   151717828+  83  Linux
/dev/sda2           18889       19452     4530330    5  Extended
/dev/sda5           18889       19452     4530298+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea0c5ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+  42  SFS
/dev/sdb2            2551       38913   292085797+  42  SFS


Thanks For the help Jim

---

### Post by ubyte on 2008-08-27
I checked and I noticed that when I added another extension on to the partition that it will not open in ubuntu. But if I didn't add to the partition that it would.

I hope this helps someone.
uByte

---

