---
title: "Installing Ubuntu along with w10"
date: 2020-07-12
forum: Installation &amp; Upgrades
---

### Post by thunderb0lt on 2020-07-12
Hello everyone, I was trying to install ubuntu on a disk that has w10 already installed, I made a partition for Ubuntu but when I was trying to make the partition table after making the first partition the rest of the space got unusable, so I couldn't continue. Any clue why is this happening? I attach a picture of the HD status. [IMG]https://ibb.co/nbNghKR[/IMG]

[https://ibb.co/nbNghKR](https://ibb.co/nbNghKR)

[IMG]https://ibb.co/nbNghKR[/IMG]

---

### Post by ubfan1 on 2020-07-12
Your W10 must be in legacy mode, not UEFI, on an MSDOS partition table type, so you are limited to only four primary partitions.  The simple way around this is to make the last partition an extended partition, then you can make more logical partitions inside that -- Ubuntu wont care.

---

### Post by Impavidus on 2020-07-12
You use MBR partitioning. That's a bit peculiar, as it's the old-fashioned way and Windows 10 computers were never sold like that, but it can happen if this is an upgrade from Windows 7 or you or some unofficial retailer installed it.

MBR partitioning comes with a limit of 4 primary partitions. Once you have 4 primary partitions, no more partitions can be made. There is a workaround: you can make one of the primary partitions an extended partition and put logical partitions inside. I don't know if the Windows partitioning tool shows the extended partition or just has you create the logical partitions. In any case, you can't have any of the existing primary partition inbetween the logical partitions.

More importantly, Windows cannot create the filesystems Ubuntu needs. So it's best to shrink Windows partitions using Windows tools, then create the Linux partitions using Linux tools. gparted is included on the live disk. Use it to create an extended partition in the unallocated space, then add the Linux partitions you want inside that extended partition, then install Ubuntu.

---

