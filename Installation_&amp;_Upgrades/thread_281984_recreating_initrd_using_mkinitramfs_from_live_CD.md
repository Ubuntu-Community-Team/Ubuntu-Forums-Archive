---
title: "recreating initrd using mkinitramfs from live CD"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by papikondalu on 2006-10-21
A long story ... This long story is to tell people not to do somethings, and also to tell my success using a crude method, and finally to know if there is another elegant solution.

BAD PARITIONING:
===============
I have a dualboot windows XP and ubuntu dapper installation. During the ubuntu installation,  I created  swap and ext3fs partitions as primary partitions. Before this installations there were already two primary partitions; one compaq_diagnostic partition, and the other winXP partition.
Thus, there were a total of 4 primary parititions.
 hda1 - compaq_diagnostics 3GB
 hda2 - NTFS 20GB
 hda3 - linux-swap 2GB
 hda4 - ext3fs 20GB
 unpartitioned space of 40GB

MISTAKE:
=======
When I tried to create another partition (to utilize the unpartitioned space for data), gparted informed that only 4 primary partitions are allowed. Already, I spent considerable time configuring the Ubuntu system  to my requirements. Thus, re-installation was not a choice. I did something stupid after that:
(1) deleted hda3 (swap) partition
(2) Made bootit-ng slide the hda4 partition to the hda2 edge
(3) Created an extended partition to hold 2GB linux-swap and 40GB data partition.

The new partition table looks like this:
 hda1 - compaq_diagnostics 3GB
 hda2 - NTFS 20GB
 hda3 - extended partition (starting after hda4)
 hda4 - ext3fs 20GB
 hda5 - linux swap 2GB
 hda6 - ext3fs 40GB (data partition)

**Never to a partition move** unless you know how to fix it.

DEBUGGING?
=========
After this change, ubuntu did not boot. It still thinks that the swap space is in hda3. I changed fstab. It did not help. Looks like swap partition is used for initramfs/initrd. After a long web search, I realized that the problem is related to initrd. All my attempts to create a new initrd image using mkinitramfs failed. The documentation I encountered suggested that I should do a "dpkg-reconfigure kernel..." to recreate the initrd image. I could not do that because my current root is not /dev/hda4. _Is there a way to mount /dev/hda4 as the root after booting into the live CD mode_?

MY CRUDE SOLUTION
=================
(1) Tar all the contents (with file and user permissions) and store the archive in hda6 (say in TAR1)
(2) Re-install ubuntu again on hda4 with the pointers to swap in hda5
(3) tar the boot directory and backup to hda6 (to BOOT_TAR)
(4) untar TAR1 into hda4, and next BOOT_TAR to hda4. 
The above long procedure is to use my configuration with a initrd for the current partition table. Now, everything works.

ELEGANT SOLUTION
================
Is a good solution just to do a "dpkg-reconfigure ... " or a "mkinitramfs ..."? I could not do the first becase the root was differnt. mkinitramfs failure appeared to be the same (don't know the exact reasons for failure).

Is there a way to mount hda4 as a root after booting into live CD? 

Is there a way to update initrd image using mkinitramfs after booting into the live CD?

Thank you for reading a looong mail. The answers to the last question would be a good learning for me.

-PK

---

