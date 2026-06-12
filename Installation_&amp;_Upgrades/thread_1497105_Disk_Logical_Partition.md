---
title: "Disk Logical Partition"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Nikolas Kleanthous on 2010-05-30
Hi
I installed Ubuntu from a cd to my computer as a secondary operating system. That is i have both windows and ubuntu. During the installation i tried to create a separate logical partition for ubuntu. Unfortunately this did not happen so i have 2 operating systems on one logical drive. How can i split the partition to the two operating systems? Also windows does not see the installation of ubuntu but on the other hand ubuntu can access my windows files. Why does this happen ? 

Thank you, 
Nikolas

---

### Post by darkod on 2010-05-30
Unless you installed wubi inside windows, you can't have them on same logical partition (and that's partition, not drive, although MS uses the term drive, a drive is a disk, partitions are parts of the same physical disk).

Windows can't see it because it's designed not to see any linux installations.

From ubuntu, you can always get a list of your disks and partitions with running in terminal:

sudo fdisk -l (small L)

---

### Post by ajgreeny on 2010-05-30
Yes, I think you are confusing logical partitions and drives.

Windows has to be in a primary partition or it will not boot.  Linux can be in any type of partition and still boot with no problems, as long as the boot manager is set up properly, of course, and normally in linux that is grub, or now grub2.

Report back here the output of that fdisk command from darkod and it will be easy to tell you if all is well with the system.  This all depends on your ability to boot both OSs, of course, so tell us if that is possible as well.

---

