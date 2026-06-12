---
title: "Ubuntu boot problem on external hard drive"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by Tansu_zel on 2013-10-20
Hello,

My problem is with the boot of Ubuntu 13.10 x86.

I installed Ubuntu on the second partition (logical partition) of my external hard drive. But It can't boot. Grub goes to the rescue mode and says "no such partition".

Partitions in GParted:

[http://postimg.org/image/9oty584cv/](http://postimg.org/image/9oty584cv/)

I tried many ways with GParted and Boot Repair to solve this problem. And the last one is on this page:

[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

It didn't work either.

Here is the report from Boot Repair:

[http://paste.ubuntu.com/6272668/](http://paste.ubuntu.com/6272668/)

I have Windows 8.1 on my computer and I want to use Ubuntu on my external drive, if I need Ubuntu.

Thanks for your help.

---

### Post by oldfred on 2013-10-20
If you are going to add a separate /boot it needs to be near beginning of drive. Usually not required except some very large external drives.

Grub supposedly fixed a bug where it would not boot from very large / (root) partitions, but some combination of BIOS, USB drivers & grub do not work unless a separate /boot or all of / is inside the first 100GB  (rest of drive can be /home or other data partitions) of a USB drive.

---

### Post by Tansu_zel on 2013-10-20
Should I put the Ubuntu-Partition to the beginning? Is it not possible to have the 884GB partition in the beginning and Ubuntu-Partition after that, to boot Ubuntu?

---

### Post by oldfred on 2013-10-20
That seems to be an issue with some BIOS and USB booting with grub not correctly finding partition. 

If you make changes to move the NTFS partition be sure to run chkdsk on it immediately afterwards. Moving a large partition like that may take a long time, so not interrupt or you will corrupt data. Be sure to have good backups first.

---

