---
title: "Installation and Hard Disc problems"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by The last Bert on 2006-08-26
Hi,

I'm fairly new to Linux, but I use Dapper on my PC, and get on with it very well. When I tried to install it on another pc though, I came across a lot of problems:

1. Using the LiveCD and attempting to edit the partitions manually, the swap and the / partition from a previous install have a padlock symbol next to them, and seem to imply they are mounted. Why is this? If I am running from the liveCD, shouldn't I be able to delete all the partitions on this drive and make new ones?

2. If I create new partitions along with the ones I can't delete, and tell Ubuntu to install to the new partitions, it all works fine. The PC also has a second hard disc though, and when I boot ubuntu up, it is not mounted. I looked in System>Administartion>Discs and the drive and its two partitions are listed, but even if I format them, give them and access path and click 'enable', nothing happens, and the partition(s) are listed as inaccessible.

Any help would be greatly appreciated

Thanks

Brett

---

### Post by Original Brownster on 2006-08-26
Hi,
1/ I havent run the live cd for a long time so cant remember for sure but I would think the live cd creates 2 mountpoints for itself, these would be locked, what are they labelled? normally they have some /dev/ name and would be a ram disk (possibly) and a cdrom mount point for the live cd.


2/ I just tried the disk manager tool to mount a partition and it seems to work however it's a temporary mount that will not mount again at next boot.
If you want to have the partitions mount each time you boot you need to edit the file /etc/fstab
I can help you do this if you like, open a terminal window and at the prompt type:
less /etc/fstab
paste the output into your reply and also let me know the partition names of the 2nd disk, should be something like /dev/hdb1 /dev/hdb2 for ide disks or maybe /dev/sdb1 for sata disks.



> **The last Bert said:**
> Hi,

I'm fairly new to Linux, but I use Dapper on my PC, and get on with it very well. When I tried to install it on another pc though, I came across a lot of problems:

1. Using the LiveCD and attempting to edit the partitions manually, the swap and the / partition from a previous install have a padlock symbol next to them, and seem to imply they are mounted. Why is this? If I am running from the liveCD, shouldn't I be able to delete all the partitions on this drive and make new ones?

2. If I create new partitions along with the ones I can't delete, and tell Ubuntu to install to the new partitions, it all works fine. The PC also has a second hard disc though, and when I boot ubuntu up, it is not mounted. I looked in System>Administartion>Discs and the drive and its two partitions are listed, but even if I format them, give them and access path and click 'enable', nothing happens, and the partition(s) are listed as inaccessible.

Any help would be greatly appreciated

Thanks

Brett

---

