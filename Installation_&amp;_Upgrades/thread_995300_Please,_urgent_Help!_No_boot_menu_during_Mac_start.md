---
title: "Please, urgent Help! No boot menu during Mac startup"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by kartal on 2008-11-27
Hi

I have installed Ubuntu on my Macbook. Now I do not have any mac boot startup at all. I had one ntfs and one ext2 partitions before Ubuntu setup. I have used guided partition. I checked out the drive with gparted after install and the partitions seem to be there. But I cannot be sure about the content. How can I fix  the boot menu problem?(assuming that it is a boot problem)  I actually do not even see the macos either, pretty much gray screen.


thanks

---

### Post by CTRLurself on 2008-11-27
did you install OSX to NTFS (not smart), or delete your HFS (journaled) partition (really bad)?

Under either condition you will want to be sure that your OSX partition is HFS journaled (and present). You may need to use the OSX restore disks you were given with your macbook.

then follow the instructions here: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) it'll work almost perfectly with Ubuntu 8.10, only minor (and obvious) changes/differences

Hope this helps.

---

