---
title: "Tip: Check for bad blocks before installing Linux!"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by illegalbuds on 2008-11-25
If you own an old PC or laptop this is a must. If you don't you may find yourself repeatedly installing Linux or migrating back to Windows. It just won't boot, and if it does boot you may be wondering why you're receiving so many I/O errors. You have corrupt blocks on your hard disk! Hard disks go bad and replacing them is costly, so for all you people who can spare a couple megabytes, keep reading!

Okay, so you've loaded up the LiveCD. Now before clicking Install, start up GParted and make your partitions. Normally, I have /boot (1GB), root / (10GB) and the rest is for /home.

Because I like ReiserFS, I need to use badblocks rather than adding a -c (or 2 c's for a slower, better scan) option in mke2fs. Oh BTW, I save the file lists (from badblocks) on a USB disk.

I would run something like:```
# mke2fs -c -c -L boot /dev/sda1
# badblocks -v -o /media/disk/root.txt /dev/sda2
# badblocks -v -o /media/disk/home.txt /dev/sda3
# mkreiserfs -l root -B /media/disk/root.txt /dev/sda2
# mkreiserfs -l home -B /media/disk/home.txt /dev/sda3
```*Note: Running badblocks may take many hours. Actually, my home partition which is about 100 gigs took me a couple days!*

By now, it's safe to Install. Be careful though, you need to setup the manual partition with Format **unchecked** for boot, root and home partitions. 

Hope this helps!

---

