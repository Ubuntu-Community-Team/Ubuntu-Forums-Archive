---
title: "Grub2 and Windows partitions"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by geohei on 2010-05-07
Hi.

I upgraded from 9.10 to 10.04 (no fresh install, an upgrade). During the upgrade, the installer asked me for the harddisks and partitions to include. I gave him the following ones:

harddisk 1
1. Windows XP
2. Windows 2000

harddisk 2
3. Ubuntu 10.04

After the installation was complete, I could only start Ubuntu. Both Windows versions just showed a flashing cursor at the left upper top screen. No HDD activity!

What went wrong?
How can I get WinXP and Win2000 selectable within grub2?

BTW, neither Google, nor help.ubuntu.com could help so far.

Thanks,

---

### Post by oldfred on 2010-05-07
Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This is what the instructions say (bold by me):
If you're unsure which **drive** is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is **not recommended**.

It then presents a check box with all **drives and partitions**. So everyone (And I think it its everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc.

Windows keeps essential boot data in its PBR partition boot record or boot sector. So you overwrote part of windows boot.

---

### Post by geohei on 2010-05-08
This worked! Great!
Thanks a lot !!! :))

Bye,

---

