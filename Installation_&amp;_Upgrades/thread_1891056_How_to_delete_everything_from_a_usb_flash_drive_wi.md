---
title: "How to delete everything from a usb flash drive with ubuntu installed on it?"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by computerboy on 2011-12-04
Well, the title says it all, but I installed Ubuntu 11.04 on a flash drive and it didn't work very well, and now I want to delete ubuntu from the flash drive but Ubuntu won't mount it.  Any Ideas?

---

### Post by fdrake on 2011-12-04
> **computerboy said:**
> Well, the title says it all, but I installed Ubuntu 11.04 on a flash drive and it didn't work very well, and now I want to delete ubuntu from the flash drive but Ubuntu won't mount it.  Any Ideas?

post:
```

sudo fdisk -l

```

---

### Post by C.S.Cameron on 2011-12-05
If you did a Live USB and it is formatted FAT then a re-format in Windows or Linux should work.

If you did a Full install and there are multiple partitions, do not format with Windows, it only sees the first partition of a flash drive.

Use gparted, it is available on the Live CD.

---

### Post by computerboy on 2011-12-05
Well, nothing seems to pick the flash drive up.  That's the problem.

---

### Post by efflandt on 2011-12-05
If **sudo fdisk -l** does not show something about it and gparted cannot find it (top menu on left selects which drive), insert it while running a Linux system or live system on install CD or iso on USB, and see what the end of **dmesg** says about it.

If you accidentally formated the entire flash (like sdb instead of sdb1) instead of a partition, use gparted to create an **msdos partition table** on it and then whatever partition(s) you want.  I have done that more than once when I clicked the wrong thing (drive instead of partition) to format in Startup Disk Creator.

---

