---
title: "Can only boot off HD (Grub) with liveCD"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by tommycli on 2007-09-25
I just installed Kubuntu. I have /boot and / on separate partitions.

My hard drive isn't detected as bootable. However, when I run the LiveCD and select "Boot first hard disk", grub loads and I can boot into my installation.

I've already tried restoring grub with the following commands:

```

grub
find /grub/stage1
root (hd0,0)
setup (hd0)
quit

```

```
root@monolith:/home/tommycli# fdisk -l

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c4c9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          38      305203+  83  Linux
/dev/sda2           18388       30515    97418160    5  Extended
/dev/sda5           18389       22332    31680180   83  Linux
/dev/sda6           22333       30022    61769893+  83  Linux
/dev/sda7           30023       30515     3959991   82  Linux swap / Solaris
```

---

### Post by rsambuca on 2007-09-25
You can use gParted on the liveCD to restore the bootflag option onto your hard drive.

---

### Post by tommycli on 2007-09-26
That was definitely it. Thanks a lot.

---

### Post by rsambuca on 2007-09-26
Good stuff!!!

Mark the thread as [Solved] under thread tools.

---

