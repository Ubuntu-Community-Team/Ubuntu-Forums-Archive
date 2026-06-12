---
title: "Problems after copying of the Ubuntu Partition"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by mahy on 2010-04-02
Hello people,

I've got a really peculiar problem. I had a Vista partition on my HDD, and behind it an 'extended' partition containing one reiserfs partition with Ubuntu and one swap partiton.

Then I removed the Vista partition using Gparted and copied the contents of the ubuntu partition to the freed space where Vista was. Well, now I have two almost identical Ubuntu partitions (the newer one is bigger), but I can only boot the old one! I don't know how to adjust grub, uuid and related stuff. Please pleas, if you have any ideas, don't hesitate and write them.

This is the outcome of the fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d67f572

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11047    88734996   83  Linux
/dev/sda4           11048       19457    67553325    5  Extended
/dev/sda5           11048       18936    63368361   83  Linux
/dev/sda6           18937       19457     4184901   82  Linux swap / Solaris

```

---

### Post by mahy on 2010-04-02
Oh, don't bother, I figured it out. First, I had to change the partition's UUID using reiserfstune, because the two partitions had the same UUID, which was the root of all evil. Then I booted the new partition (had to manually modify Grub commandline at bootup), and ran "grub-mkdevicemap" followed by "grub-install /dev/sda1" and "update-grub". :)

**EDIT:** Now that I think about it, I could have saved myself quite a lot of work by only changing the UUID of the **old** partition (the one I planned to remove afterwards). That way, my system would probably automatically boot into the new partition and then running just "update-grub" would fix everything.

---

