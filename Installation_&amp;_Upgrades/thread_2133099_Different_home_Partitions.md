---
title: "Different /home Partitions"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by cweinhofer on 2013-04-07
I currently have Lubuntu 12.10 installed on my computer in a dual boot  configuration with Win 7. I mostly access it by loading the Linux  partition with a mapped vmdk in VirtualBox, but sometimes I do boot into  it directly.

I would like to move /home to a separate partition.  In order to back up this data along with the rest of my Windows files  without a lot of fuss, I would like to store /home in a virtual disk.  The problem is that when I boot directly into Linux, this virtual disk  will not be available.

With the way I use things, not having the  normal /home data available when booting directly into Linux is not a  problem, but I wasn't sure what Linux would do? Is it possible /  advisable to create second /home partition that would be used for direct  booting?

---

### Post by dino99 on 2013-04-07
dont forget that "virtual" means "temporary"; so if you want to loose your data ...

/home : separate partition
home : simple folder inside the installed distro

---

### Post by cweinhofer on 2013-04-10
dino99, I don't understand why you think that using a virtual disk image will be more likely to endanger the data. The image can be backed up just like an image of a physical drive.

Anybody have any thoughts on how to make this work or possible alternatives?

---

