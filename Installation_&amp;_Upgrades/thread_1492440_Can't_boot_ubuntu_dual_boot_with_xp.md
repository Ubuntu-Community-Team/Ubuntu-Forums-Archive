---
title: "Can't boot ubuntu dual boot with xp"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by mikiowoko on 2010-05-24
Have a computer with xp sp3.
I tried an ubuntu install and the mbr seemed to be trashed.
Reformatted the drive and reinstalled windows xp and easyBCD
Reinstalled ubuntu without GRUB

here's the present configuration:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Device    Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30618   245931254+   7  HPFS/NTFS
/dev/sda2           30618       60802   242454529    5  Extended
/dev/sda5           30618       59864   234925056   83  Linux
/dev/sda6           59865       60802     7528448   82  Linux swap / Solaris

```
What I think I need to do is install grub in /dev/sda5, but I'm not sure if that's correct, and regardless, I'm not sure how to do that.:icon_frown:

---

### Post by oldfred on 2010-05-24
Duplicate see:

[http://ubuntuforums.org/showthread.php?t=1492437](http://ubuntuforums.org/showthread.php?t=1492437)

---

### Post by mikiowoko on 2010-05-24
cant figure out to delete duplicate. it's not solved, but solved might kill the thread quicker

---

