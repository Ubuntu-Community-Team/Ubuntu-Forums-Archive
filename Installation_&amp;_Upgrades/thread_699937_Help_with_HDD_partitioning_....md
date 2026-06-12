---
title: "Help with HDD partitioning ..."
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by kubug on 2008-02-17
Ok, here it is...

I have installed ubuntu and windows XP on my machine on a fakeraid with 2x 160GB HDD's. I love the speed this gives me, and don't want to go back to single drives.

My question is: I also need to install Vista (I need to test programs under all three operating systems) and would like it to be on the RAID.

Last time I tried, I needed to create a primary (1) for my /boot on the RAID.

I also needed to make a primary for swap (2).

Then I did a primary for "/" (3).

Which left me with ONE primary partition for Windows XP and none for Vista.

Vista kinda wants to be installed on the first partion as well.

I tried creating a primary boot and then make an extended for swap and "/" (which would only use 2 primaries), but then Ubuntu wouldn't boot anymore.

Anybody got any ideas how I could do this setup?? :confused:

---

### Post by amohanty on 2008-02-17
I am pretty sure that you should be able to install / and swap on an extended partition, here is what I have on my laptop:

07:03 PM $ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000697d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2              17        7296    58476600    5  Extended
/dev/sda5              17         259     1951866   82  Linux swap / Solaris
/dev/sda6             260        1232     7815591   83  Linux
/dev/sda7            1233        2448     9767488+  83  Linux
/dev/sda8            2449        7296    38941528+  83  Linux

As you can everything except sda1 which is /boot is on an extended partition, but then again you are using RAID. You might want to try from scratch and see if it works.

Also for testing environments where you need different 'incompatible' (windows _always_ wants the primary partition) OSs I would strongly recommend going the Xen or VMWare route. Its much easier to manage and use.

HTH
AM

---

### Post by kubug on 2008-02-18
Thanks for the reply.

I am pretty sure I tried the extended partition. For some reason, Ubuntu refused to boot this way. I still think it's a GRUB issue on SATA RAID.

At work, I use virtualbox at work to test programs. Actually, I use SSH x forwarding to start them on the main server there and use them on my computer. 

But at home here I wanted to have the 3 OS's so that I can compare 3D apps, mostly games, between the different platforms. I have an nvidia card and they work great with WINE and STEAM applications in Linux. VM's can't do 3D. So that' why I wanted them installed like that.

I will try your suggestion when Hardy comes out. Maybe Hardy will have SATA RAID install option.

---

