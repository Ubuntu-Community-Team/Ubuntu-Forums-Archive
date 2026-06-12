---
title: "partitions"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by lexxin on 2009-12-12
I am trying to install Ubuntu w/ win7. I have tried to install it automatically but Ubuntu takes too much space this way.
 
So I am trying to choose partitions manually.
what partitions I need to have to choose to install it manually.
I have normal NTFS partition but apparently I need something else.

use as: ext 4, ext3, ext2   ???
mount point: /, /boot, /home ???

thanks

---

### Post by User3k on 2009-12-12
Do it manually and just create a / directory. Ubuntu will break the rest down. Well the / , which is root, and a SWAP space. That way you can tell the installer how much space you want to use for Ubuntu. As far as file systems you can use anything you want but ext4 is the new default one.

Then as you learn you can break it down further on future installs once you understand a little more about /home, /boot, /, /var, and so on.


Edit: I keep adding to this, lol. Also it is smart to back up all your important files no matter what you are doing, whether it is in Linux or Windows, before you make changes to your hard drive.

---

### Post by darkod on 2009-12-12
Basically you need to shrink your win7 to make unallocated space for ubuntu, but you decide how much to shrink, how much to leave for ubuntu. Then just boot with ubuntu cd, select Install Ubuntu and tell the installer to use Largest Available Free space. It will not take more than what you left for it.
You could try creating partitions manually but again you need to have the unallocated space (or be ready to delete some partition to make unallocated space). The minimum you need:
1. / (root) partition, that's the system partition, size at least 25GB (if you don't plan putting big videos/music files in it), filesystem ext4, mount point /
2. swap partition, size 1.5 times your ram memory, filesystem swap, mount point swap

That's it.

---

