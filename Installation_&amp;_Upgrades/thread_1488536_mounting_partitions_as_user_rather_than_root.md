---
title: "mounting partitions as user rather than root"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Harvs on 2010-05-20
Hi

I'm having a problem mounting a vfat partition using fstab...

If I don't use fstab and mount it manually, everything works fine.

But if I add a line to fstab, it will mount, but will have root permission only - so I can't write to it.
I can mount another partition (ext4) through fstab and everything works fine.

Just not sure why there's a problem with the vfat partion. Also, if after mounting it through fstab I try to unmount it, it gives an error saying only root can unmonut it.

Any ideas??
Cheers
Harvs

---

### Post by Harvs on 2010-05-20
Ah - don't worry. I've fixed it. Needed different options on fstab.

---

### Post by Morbius1 on 2010-05-20
Post your fstab so we can see the line you use to mount the FAT32 partition.

OOPS, took too long to respond. Sorry

---

