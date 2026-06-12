---
title: "Kubuntu, cant access second hard drive. Fdisk -l shows ok"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-09-23
Dolphin wont browse my other hard drive. It shows the volume but only offers to unhide it.
Intrepid Kubuntu is installed on sdb and Hardy on sda. When I'm on Hardy i can browse sdb with nautilus just fine.

```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8484877a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460        1702     1951897+  82  Linux swap / Solaris
/dev/sda3            1703       30401   230524717+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa6e96290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1459    11719386   83  Linux
/dev/sdb2            1460        1702     1951897+  82  Linux swap / Solaris
/dev/sdb3            1703       30401   230524717+  83  Linux
```

---

### Post by 1cewolf on 2008-09-23
I've run into the same issue with my backup hard drive. Running Dolphin as root will allow you to browse your drive.

---

### Post by philinux on 2008-09-23
Cheers. I just thought I'd check out kubuntu as ubuntu was so stable LOL. Is this bugged?

---

### Post by Ryuzakii on 2008-09-23
This has already been reported. I don't have the number on hand, but I do remember seeing it.

---

