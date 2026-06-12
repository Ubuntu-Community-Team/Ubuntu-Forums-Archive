---
title: "disk partitioning problem"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by sgg on 2007-05-10
I'm trying to re-partition an external disk.
seagate 750 GB

command line method as outlined in docs works to a point:

```
vfx@jupiter:~$ sudo mke2fs -j /dev/sdg1
/dev/sdg1 is apparently in use by the system; will not make a filesystem here!
```

The drive is not mounted. It's commented out in fstab.

Gparted crashes when applying the format to the disk.

In gparted, the disk comes up as "unknown" (black)

---

