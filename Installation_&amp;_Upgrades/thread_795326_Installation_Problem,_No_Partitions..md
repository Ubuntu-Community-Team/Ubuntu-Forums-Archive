---
title: "Installation Problem, No Partitions."
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Phalangees on 2008-05-15
When running the installation, I run into a problem when setting up partitions. There is nothing that shows up under the hard drive. To the installation, the partition table appears to be nonexistent. But yet I have xp and vista both installed so I know the partition table is intact. I've even tried the alternate installation cd with the same problems. Any help on the matter would be greatly appreciated.

Thanks.

---

### Post by dstew on 2008-05-15
Are you trying to install 8.04 using the Live CD? If so, you can hopefully post to the forum a screenshot of the partitioner display. Which partitioning mode did you select? Whole disk, guided or manual?

It might also help to boot the Live CD, open a terminal window, and enter the command```
sudo fdisk -l
```That will print a list of the disk partitions as seen by the Linux kernel. Post that output to the forum.

---

