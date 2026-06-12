---
title: "dual boot windows 7 &amp; ubuntu // mount issue"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by xigen on 2010-08-28
I want my new laptop (Dell Studio pp39L) to dual boot win7 and ubuntu 10.4.

I burned a ubuntu 10.4 disk
-- checked for errors
-- checked the md5sum
-- looked at - physically -- and all is OK

I then used the disk to 'try ubuntu 10.4 without installing'.  That worked just fine... until...  windoz 7 installed updates.  After the updates my ubuntu disk would not mount:

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/Output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

...

What would you suggest I do to move forward with my install of ubuntu 10.4?

Cheers,

MW

---

### Post by Mark Phelps on 2010-08-31
> **xigen said:**
> What would you suggest I do to move forward with my install of ubuntu 10.4?

At this point, I would suggest you DON'T move forward.

Dells are notorious for coming preloaded with the maximum limit of 4 primary partitions -- making Ubuntu installation a nightmare.

To see if yours is that case, open a terminal (from LiveCD mode) and run "sudo fdisk -lu" (that's a lowercase L, not a one).

IF you see four partitions, you are in for MAJOR work to install Ubuntu (or any other Linux distro).

---

