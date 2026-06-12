---
title: "Can't change size of Ubuntu Partition"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by kayklein on 2013-01-18
I currently have my hard drive partitioned with a Windows side and a Linux side. When I installed Ubuntu on this computer a few years ago, I gave a large amount of my hard drive space to the Linux side, and not much to the Windows side. I would like to change the sizes of my partitions so they are equal (reduce the size of the Linux side and increase the size of the Windows side. 

I tried to do this by making an install disc from the Ubuntu version I'm currently running (12.04 LTS) and booting off of that. I click to create a custom installation and am able to control the size of all the partitions EXCEPT the Linux one. I do not have the option to change the size of the Linux partition (see attached pictures which show the options I have for the Windows and the options I have for the Linux partitions). How do I get the option to change the Linux partition size?

---

### Post by Cheesemill on 2013-01-19
Shrinking XFS partitions isn't possible.

Your easiest option would be to backup your data and then re-install Ubuntu onto a smaller partition.

---

