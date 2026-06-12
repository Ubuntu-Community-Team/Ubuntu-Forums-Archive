---
title: "Disk Drives not detected in Ubuntu 6.06 LTS Live CD"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by scottptn on 2007-08-28
Hi,

Im a Linux newbie and  have been using Ubuntu 6.06 LTS-The Drapper Drake Live CD for quite some 
time and would now like to install it as a dual boot with windows on my laptop.I have one hard disk of size 80 GB on my laptop which currently has Windows XP Professional on it.
However,when i proceed with the installation and reach the partitioning stage , no disk 
drives are shown.
Even GParted gives the message "No disk drives detected".
What could be the problem ?

Thanks a lot :)

---

### Post by Pumalite on 2007-08-28
Post your specs. It could be that winblows doesn't want anything else installed there.

---

### Post by scottptn on 2007-08-28
Hi Pumalite,

Thanks for your reply. Im sorry i didnt quite understand, what specs am i supposed to post . Could you please elaborate on exactly what details you need ?

Thanks :)

---

### Post by Pumalite on 2007-08-28
Motherboard? Chipset? Memory? Graphics?

---

### Post by scottptn on 2007-08-28
Well, i have 512 MB of RAM and a 80 GB hard disk which is partitioned in the following way :

1. Primary Partition of 31 GB with 20 GB NTFS C :\ , 10 GB Fat32 E:\ , and 1000 MB unallocated

2. Extended Partition of 49 GB with 35 GB allocated to 4 partitions and remaining is free space.

---

### Post by scottptn on 2007-08-28
Well, i have 512 MB of RAM and a 80 GB hard disk which is partitioned in the following way :

1. Primary Partition of 31 GB with 20 GB NTFS C :\ , 10 GB Fat32 E:\ , and 1000 MB unallocated

2. Extended Partition of 49 GB with 35 GB allocated to 4 NTFS formatted partitions and remaining is free space.

Is there any other information u need ?

Thanks .

---

### Post by Pumalite on 2007-08-28
Boot from Live CD and at the Terminal: sudo fdisk -l (small L)( of your filesystem)

---

