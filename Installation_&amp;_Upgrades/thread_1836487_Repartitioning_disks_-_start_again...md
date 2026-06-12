---
title: "Repartitioning disks - start again.."
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by Bucephalus01 on 2011-08-31
Hi there.
I'm reinstalling ubuntu server. I just installed it for the first time two days ago using guided partioning. I'm pretty sure I selected some guided LVM partioning because there are LVM partitions. 

Anyway, I want to install raid 1. I have never done this before because I'm very inexperienced with linux and general system admin, but I'm following the instructions in the ubuntu server manual.
But before I do that I just want to basically reformat both disks I have installed and start from scratch. DOes anyone know the best way to do this. I have attempted and it said for the second disk that the LVM is using part of it and so no changes could be made.

REgards
David.

---

### Post by Bucephalus01 on 2011-08-31
Actually, this is the exact message I get when I try to partition it. 

"No modifications can be made to the partition #5 of device SCSI2 (0,0,0) (sdb) for the following reasons:

In use by LVM volume group Varus"

Varus is what I called the computer during setup.

---

### Post by Bucephalus01 on 2011-08-31
I worked it out.
I had to go into the "Configure the Logical Volume Manager" option and delete the logical volumes.

Thanks for reading.

---

