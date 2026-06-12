---
title: "RAID 1 Server Install - No File System Error"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by ghanson59 on 2014-05-17
Darkod -
Your post here [http://ubuntuforums.org/showthread.php?t=2109438&p=12477248#post12477248](http://ubuntuforums.org/showthread.php?t=2109438&p=12477248#post12477248) saved me!
I'd been going round and round setting up and tearing down my 12.10 LTS then 14.04 LTS server install.  It wasn't until I stumbled upon your succinct directions for creating the partitions using GParted (I went for GPT rather than MS-DOS) and setting the flags before running the server install that I was able to "get it."
I'd seen a number of posts regarding the issue with grub2 not getting loaded properly or the file system not being set by the installer (even when using Guided) but none explained precisely how to set the partitions.  Your directions put me on track and now my RAID 1 is up and running.

Thanks for helping me avoid tearing out the **rest** of my hair! :D

Greg

---

