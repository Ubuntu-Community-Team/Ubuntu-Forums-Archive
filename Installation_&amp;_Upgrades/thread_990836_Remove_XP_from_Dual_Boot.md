---
title: "Remove XP from Dual Boot"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Lupgaru on 2008-11-23
I have XP and Ubuntu on my laptop and I want to uninstall XP and reclaim disk space. 
    How would I do that?

---

### Post by glotz on 2008-11-23
First, congratulations!

It's real simple. The easiest way probably is to use a partition editor to remove the fat or ntfs partition the windoze is on and any other now useless partitions related to it. Then you can make a new partition with e.g. the ext3 file system. Finally, remove any entries from the grub menu related to windoze. That's in /boot/grub/menu.lst.

It's probably a good idea to get the latest version of gparted from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

(I wrote this assuming it's a normal Ubuntu install from a CD to a partition(s) of it's own. If you used wubi or some other special setup, you'll probably need to do something different.)

---

