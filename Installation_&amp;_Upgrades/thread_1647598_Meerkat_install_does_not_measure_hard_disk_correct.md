---
title: "Meerkat install does not measure hard disk correctly"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by rhdinah on 2010-12-17
I've been trying to install 10.10 Meerkat onto a new machine. I've tried alternate and desktop. In each case the install will not proceed because the installer claims that my hard disk is less than 2.6GB. Indeed it is 100GB and is recognized properly by BIOS. Win 7 installs correctly.

Mobo: [Asus P7H55-M PRO]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131623") (H55 chipset)
Processor: Intel i5-650
Memory: 4GB Corsair XMS3

I cannot find a similar post so if there is one and someone can point me to it please do. :D I need some help in bypassing this and proceeding with the install. Thank you for your interest and replies!

---

### Post by dabl on 2010-12-17
Could be a number of things, including SATA mode setting in BIOS.  Take a look at #1.b. here: [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

Also, trying doing the partitioning in advance, with a Parted Magic or GParted Live CD.  Then use the Ubuntu Alternate Install CD, choose "manual" partitioning, and simply choose the partitions that you have already prepared.

---

### Post by rhdinah on 2010-12-18
> **dabl said:**
> Could be a number of things, including SATA mode setting in BIOS.  Take a look at #1.b. here: [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

Also, trying doing the partitioning in advance, with a Parted Magic or GParted Live CD.  Then use the Ubuntu Alternate Install CD, choose "manual" partitioning, and simply choose the partitions that you have already prepared.

Thanks I'll give that a try. I'm not sure if it is so much a measurement problem as it is device recognition. The LTS Desktop version 10.04 works it appears. I might just install that and do an upgrade to the next version. At any rate I'll try those suggestions. I wish Ubuntu would come out with a ".1" version before too long. That really helped with the LTS release. Thanks for your reply!

---

### Post by psusi on 2010-12-18
How large does it think it is?  What is the output of sudo fdisk -lu?  Are you doing a full disk install, side by side, or manual partitioning?

---

### Post by rhdinah on 2011-03-02
Exchanging motherboards and other ancillary moves to solve this created no solution. So just for fun I took the system in for 'repair' citing many reasons that Windows 7, Ubuntu, Fedora and the like wouldn't install correctly. I put an old CDROM drive into the machine rather than using a USB key install to make their life easier. $150 later they claimed that the CDROM drive was defective ... which, of course, had nothing at all to do with the original problem. They replaced the CDROM drive which, all of a sudden, allowed Windows 7 and Ubuntu to load. I brought the system home with my tail between my legs. At home I tried to load Ubuntu again from CD ... like I needed Windows 7 on a partition ... it worked. And then again just for fun I tried to load Ubuntu with the USB key and it worked! Blimey I thought ... it somehow miraculously fixed itself. No complaints really, but what the H-E-double chopsticks happened to the original problem? LOL!

---

