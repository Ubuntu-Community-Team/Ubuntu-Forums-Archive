---
title: "My ubuntu cant read my HD!!!"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by azndreamer781 on 2007-06-03
Please help me. is there any way for my ubuntu to read my window install hd and my other hd.
i only have 1 hd but i make it into 3 partition 1 for window xp and 1 for my personal stuff and 1 for ubuntu. wut do i use to read the other hd?

---

### Post by jfinkels on 2007-06-03
> **azndreamer781 said:**
> Please help me. is there any way for my ubuntu to read my window install hd and my other hd.
i only have 1 hd but i make it into 3 partition 1 for window xp and 1 for my personal stuff and 1 for ubuntu. wut do i use to read the other hd?

Many Windows partitions use the NTFS filesystem, which is not natively supported in Ubuntu. To have read and write access to your NTFS partitions, use the ntfs-3g driver. Follow this how-to for NTFS read/write support: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

To view information about disks and partitions installed on your system, type the following in the terminal:```
sudo fdisk -l
```

It will show you a listing of disks (like /dev/sda) and partitions on each disk (like /dev/sda1, /dev/sda2, and so on).

---

