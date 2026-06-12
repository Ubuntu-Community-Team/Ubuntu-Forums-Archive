---
title: "partitioning help"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by rkd1312 on 2007-05-28
I have decided to put ubuntu on my desktop as a dual boot i have two HDD one 20gb and one 200gb i need to put the partition for ubuntu on the 20gb but when the partition screen comes up on the instal wizard of the live disc the drive that is shown is he 200gb one

---

### Post by meng on 2007-05-28
Is this a graphical installer? There may be a drop-down menu list somewhere in the upper-right corner that allows you to select another disk, e.g. hdb or sdb rather than hda/sda

---

### Post by rkd1312 on 2007-05-28
i think there might be an easier way if some could just help me partition the 20gb drive so i could install it regularly. oh and before i was using the install option on the live cd

---

### Post by louieb on 2007-05-28
If the 20 gig drive does not show on the first screen you have two choices. One is to use the manual partitioning option. That option uses the partitioner GParted. GParted is easy to use but its not foolproof. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")  you need to be careful. 

The other option  is to unplug the 200 gig drive, Install Linux, plug the 200 gig back in, configure GRUB to boot windows or use BIOS to switch operating system,  lots of things to work through, but at least the 200 gig drive is not changed. 

Setting up a PC to dual boot is not like installing a game in windows. Sometimes its almost that easy. Just remember before you start backup anything you want to keep. If you or the installer makes a mistake .... well  your computer will make a nice doorstop.

---

