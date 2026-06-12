---
title: "expanding extended partition"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Hauke on 2007-04-27
Hi

I want to reorganize my partitions on my hard disk and there is a extended partition but it is too small for my needs and I can't delete it because Ubuntu is installed in it. 

With the Ubuntu 6.10 CD and qtparted I was able to make the extended partition bigger to the end but I can't change the starting point of this partition. The starting point should be either some gigabytes before or after the place where it is now.

---

### Post by Thingymebob on 2007-04-27
get gparted (liveCD) and boot your system with that. This won't mount any of your partitions so you can pretty much do what you want with them. Gparted will shuffle the data in the partition around so as it all stays in tact. You should be ok from there on in
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

---

