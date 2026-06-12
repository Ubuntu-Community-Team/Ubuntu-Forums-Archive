---
title: "Problems with preparing partitions"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by al2six on 2007-12-29
I'm trying to partition my hard drive so I can have XP and Ubuntu. During the Ubuntu installation process, I selected the manual partitioner and shrunk down the partition currently used by XP to 10GB and used the remaining 46GB of free space to make a new partition for Ubuntu. But when I hit forward, I get the following error:

"File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 28034 (55960 expected); size of FATs is 110 sectors (219 expected)."

I'm new to this stuff so I don't really even understand what that all means. Any advice?
thanks

---

### Post by Pumalite on 2007-12-29
Use Gparted Live CD, burn the image to disk, boot from it and resize your XP partition (right click on XP partition; choose 'resize' from the menu): [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Defrag and back up first.

---

