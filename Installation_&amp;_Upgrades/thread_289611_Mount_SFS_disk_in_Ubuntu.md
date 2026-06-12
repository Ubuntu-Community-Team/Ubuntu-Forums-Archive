---
title: "Mount SFS disk in Ubuntu"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by ephie on 2006-10-31
hi robertwoes,

I got my hda1 (ntfs) mounted as read only. Apparently I won't be able to write on it....

Now I would like to get my second HD mounted (hdb1) but it's formated as SFS:

```

root@fanny-desktop:/mnt/hdb1# sudo fdisk -l

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3451    27720126    7  HPFS/NTFS
/dev/hda2            3452        7308    30981352+  83  Linux
/dev/hda3            7309        7476     1349460    5  Extended
/dev/hda5            7309        7476     1349428+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666   42  SFS


```

How can I mount a SFS and can I get read AND write access to it?

thank again for your help!

eph!e

---

### Post by robertwoes on 2006-11-05
[http://ubuntuforums.org/showthread.php?p=1716349#post1716349](http://ubuntuforums.org/showthread.php?p=1716349#post1716349)

---

