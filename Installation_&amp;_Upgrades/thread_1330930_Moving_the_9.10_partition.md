---
title: "Moving the 9.10 partition"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by tonyr on 2009-11-18
My current working version is 8.04, which is on a partition on the first drive, sda3.  I have installed 9.10 on a partition on the second drive, sdb11.  Grub2 is installed in the boot sector of the 9.10 boot partition.  I'm using grub-legacy with 8.04, and booting into 9.10 with a chainload stanza in menu.lst.

Now I want to move the 9.10 installation to a partition on the first drive, sda2.  I have copied the partition contents with (mounted partitions)
> cp -a /media/sdb11 /media/sda2
and that seems to be fine, after a little housekeeping. I copied the boot sector from the original partition, sdb11, to the boot sector of the new partition, sda2.  I know that grub2 organizes things differently, and that some specific location information is hardwired into the boot stage images, if I understand things correctly.  It's not clear to me that the stage1_5 image is still in the partition sectors after the boot sector, but even if it is, moving that would not solve the hardwired location

What,if anything, can I do to get the Grub2 boot information set up correctly for the new partition without reinstalling 9.10?  Do the grub2 commands have enough flexibility to handle this situation? I am currently trying to figure that out myself.

- tony

---

### Post by tonyr on 2009-11-18
The method for grub2 recovery described [here]("https://help.ubuntu.com/community/Grub2"), section 11 'Reinstalling Grub 2', does the trick.  I used the **chroot** method.

---

