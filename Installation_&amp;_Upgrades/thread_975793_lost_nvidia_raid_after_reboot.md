---
title: "lost nvidia raid after reboot"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by janeinar on 2008-11-08
In my server I have 3 disks, one for system and two in raid0 for samba data files.

After I upgraded from 6.06 to 8.04 I lost my raid, but after a while I was able to mount it again. I found that the link to the hardware raid in /dev/disk/by-uuid was wrong:

```
lrwxrwxrwx 1 root root 10 2008-11-06 22:57 21e44de9-cut-2c61cf61ed36 -> ../../sda2
lrwxrwxrwx 1 root root 28 2008-11-06 22:57 23907c72-cut-991304691c59 -> ../../mapper/nvidia_gdejddeh
lrwxrwxrwx 1 root root 10 2008-11-06 22:57 3bdbdec4-cut-fac47b2420d9 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-11-06 22:57 a5d59670-cut-64146be3e4f9 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-11-06 22:57 b584fb6a-cut-4255cd994869 -> ../../sdb1 #wrong should be ../../mapper/nvidia_gdejddeh1
lrwxrwxrwx 1 root root 10 2008-11-06 22:57 c5e676ff-cut-de3fa747c963 -> ../../sda3
```

But after "ln -sf ../../mapper/nvidia_gdejddeh1 b584fb6a-f7a0-4080-9034-4255cd994869" I was able to "mount /srv" and found all my data :D

I am sure this is not the proper way to fix the problem, and it is not the permanent way to fix it; after next reboot, I have to do these manually steps again. 

:confused: What is the proper way to fix this problem?

---

