---
title: "Ubuntu breaks Windows 7 after every boot"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by shamushand on 2010-12-05
I currently have a Windows 7/Ubuntu/Mac OS triple boot. However, every time I boot into Ubuntu 10.10, then boot into Windows, it fails to boot until a chkdsk is run. I see no particular reason this should happen, is there a way to either patch this, or to prevent Ubuntu from accessing the NTFS partition? I think this is where the problem is focused.

---

### Post by Sef on 2010-12-05
First let's check how you partitioned your machine.  

Applications > Accessories > Terminal

then copy and paste this command:

```
sudo fdisk -l
```

copy and paste the results here.

---

### Post by shamushand on 2010-12-05
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9b3496e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
/dev/sda2              13       42580   341913600    7  HPFS/NTFS
/dev/sda3           42580       45894    26622976   83  Linux
/dev/sda4   *       45894       60802   119743488   af  HFS / HFS+

---

