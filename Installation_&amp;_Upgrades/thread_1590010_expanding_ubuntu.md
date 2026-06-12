---
title: "expanding ubuntu"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by redlinethecar on 2010-10-07
How would I go by expanding my ubuntu partition over Windows 7 and taking it completely out of the GRUB boot loader? BTW I am running Ubuntu 10.04.

---

### Post by drs305 on 2010-10-07
Do you mean taking Windows out of the bootloader?

You would run the LiveCD and use Gparted to delete the Windows partition. You would use the LiveCD since none of the partitions can be mounted when you perform these partitioning chores.

If both Windows and Ubuntu are primary partitions, you would then just expand the Ubuntu partition to fill the unallocated space.

If Windows was a primary partition and Ubuntu was in the extended partition (for instance sda5) you would have to expand the extended partition first, then expand the Ubuntu partition within the extended partition.

If you provide a snapshot of the Gparted screen we can be more specific (or we can muddle through with the results of the command "sudo fdisk -l" (lowercase L).

I wrote a guide for expanding the Ubuntu /, which covers much of what you want to do. It was written for a bug in Jaunty, so you can start reading about 1/3 of the way down the first post.

[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by redlinethecar on 2010-10-07
Wow thanks a lot. I have no idea how I missed that one. Thanks so much.

---

