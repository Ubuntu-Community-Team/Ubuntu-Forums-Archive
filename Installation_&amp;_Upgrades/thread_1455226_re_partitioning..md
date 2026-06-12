---
title: "re partitioning."
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by mskin on 2010-04-15
i have a dual boot system 9.10 and XP.  the hard drive is 234. For some reason during the install i only allocated 128 to windows and 16 to ubuntu. or at least, gparted tells me i have 127.99 NTFS and 104 unallocated (=231G ??). 

system monitor tells me i have the following:
/dev/loop0 is ext4 = 16 G total
/dec/sda1 is host = 128 G total
this is 134G total

From windows, the partitioner tells me the same.  i have 104 of unallocated disk space, and 128 of NTFS.  i assume the 16 g allocated to ubuntu is inside the 128 G?.

so the question is, how do i get that additional 104 into ubuntu without screwing up the MFT of windows.  or can i?  is it as simple as telling gparted to format the space? or will that mess windows up?

thanks  for the help in advance.

---

### Post by zvacet on 2010-04-15
Did you install Ubuntu with Wubi?If you did then Ubuntu is in side Windows.If not then you have Ubuntu on separate partition,but during install you give it just 16Gb of space.If this is a case that download [Gparted live Cd]("http://gparted.sourceforge.net/") and with it expand your Ubuntu partition on unallocated space.Even better you can create separate home partition on that unallovated space so your files/settings will be safe in case of fresh install.To make separate home follow [this]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") guide.

---

### Post by 2hot6ft2 on 2010-04-15
A screenshot of GParted might help. Did you do the install inside windows aka WUBI? Or a real install to hard drive? Because it doesn't sound like a real install.

---

