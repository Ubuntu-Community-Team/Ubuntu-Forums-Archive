---
title: "large root partition"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by abraxas334 on 2010-02-25
Hi,
I have the following problem. I want to install from scratch or change a current system, which ever works best to have the following partitions:
I have a 160GB HD and want a 50GB root partition 3 GB swap and the rest for home.
When i go throught the guided partitioning process the largest i can get is 8GB.
The root partition is the bootable partition correct? How do i best go about in achiving this kind of partitioning?

Thanks for any help/comments!

---

### Post by giammy on 2010-02-25
Hi,

perhaps there are other partitions.
Do you want to delete them?

If you post the output of the command

fdisk -l /dev/sdxx

we can see what there's in the disk!

bye
giammy

---

### Post by abraxas334 on 2010-02-26
Hi thanks for the reply. I have now worked out if i delete all the partitions and don't let the automatic partitioner partition things i could get all the partitions i wanted manually :)

---

