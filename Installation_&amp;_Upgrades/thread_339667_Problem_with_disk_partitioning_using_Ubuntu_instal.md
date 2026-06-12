---
title: "Problem with disk partitioning using Ubuntu installer"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by g0nzo on 2007-01-16
Hi,

I had 2 NTFS partitions and decided to install Kubuntu. I created additional ext3 and swap partitions using partitioning app that comes with installer, however after installation I had problem with my disk and partition table. Thanks to Christophe Grenier and his TestDisk program it turned out that my NTFS partitions were created using 16 heads (whatever that means) and Kubuntu installer creates partitions using 255 heads by default. Maybe Ubuntu developers could add advanced option to the disk partitioning app to allow changing this value? Or if there are already other partitions on the disk, try to find this value and use it instead of the default 255?

---

