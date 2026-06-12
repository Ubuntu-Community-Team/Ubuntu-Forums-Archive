---
title: "Replacing HD, trying to use Ghost..."
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by mtelewicz on 2007-04-12
So I'm currently running Dapper using LVM.  My hard drive is acting like it is going to fail, so I'm trying to move all my data from one hard drive (~160 gigs) to a larger hard drive (250 gigs).  Both are SATA drives.

I've duplicated the partition table like so:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       30401   243947025    5  Extended
/dev/sda5              32       30401   243946993+  8e  Linux LVM
```

Note that this is exactly the same as the original partition table, however the Extended "8e" type partition is now larger.  I used Ghost to copy the information from one partition to the other.  All the data is intact.  However, the total space available is still the original amount of space:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Ubuntu-root
                     150532340 134926264   7959460  95% /
```

I'm under the impression that this has something to do with LVM, but I'm not very familiar with how LVM works.  I tried using lvresize and lvextend to increase the size of the logical volume, but to no avail.  I get the following (here I'm trying to increase it by just 1 extent):

```
mike@bigpimpin:/$ sudo lvextend -l +1 /dev/Ubuntu/root
  Extending logical volume root to 145.85 GB
  Insufficient suitable allocatable extents for logical volume root: 1 more required
```

Any ideas?  I'll be glad to provide any more information that you'll need.  Thanks!

---

### Post by mtelewicz on 2007-04-12
I realize now that I may have posted this in the wrong section.  Please move if necessary, and sorry :confused:

---

