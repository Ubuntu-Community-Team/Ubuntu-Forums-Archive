---
title: "Installation on existing partitions"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by vincente on 2006-06-26
Hi all,

I have 2 physical harddisk at the moment.
First harddisk 20GB - Windows XP installation (/dev/hda1)
Second harddisk 40GB - Partition into 2 separate drives. 20GB each.  (/dev/hdb5) and (/dev/hdb2)

Currently /dev/hdb5 has data and /dev/hdb2 is empty and i would like to install the OS onto this partition.

During the mounting dialog during installation, they asked me to put the root and the swap space.

So i put the root / and assign to /dev/hdb2
The swap assign to /dev/hdb5 

I proceed on to installation and they prompt me saying that the swap partition has some errors. 

Am i doing the right thing?
Appreciate any advice..

---

### Post by jasutton on 2006-06-26
I wouldn't give Swap that much space.  You usually don't want to give it any more than 1.5x your physical memory (that's just my opinion, but you'll hear varying numbers on that topic).  It might be a good idea to just select the hard drive you want to install it on, and let the installer take care of the partitioning. ;)

---

### Post by vincente on 2006-06-26
So you would suggest i get the installer to install onto the 2nd physical hard drive and let it take care of the partitioning? But currently the 2nd physical hard drive has already partition into 2 drives and one of it contains my data. 

Would it erase my data?

Another qns here, what exactly does the swap drive does? Just a temporary storage for installation?

---

### Post by jasutton on 2006-06-26
A swap partition is the same idea as the pagefile in window$.  That is, it's a piece of the hard drive that the OS can use as memory if it needs a little extra.  It's generally desirable for the OS to use physical memory (RAM) as much possible, but sometimes your computer needs more memory then it actually has.

I would recommend moving the data you have off to another location (the first hard drive would be good if you have room on it) and let the install re-partition the drive automatically.

---

### Post by gobot on 2006-06-26
I have the same problem. Xubuntu Live CD runs fine (except screensaver crashes a lot) I clicked the Install to Disk icon on the desktop. I have Windows, Gentoo, and Zenwalk on the drive, want to add Xubuntu to swap and /hda11 and /hda12.  Yes, I can pick / => /hda12 and /boot => /hda12, and erase all the other partitions from the list, but then the installer says somthing to the effect that it will erase my other partitions. Interface is not intuitive for me - anyone seen installation docs regarding existing partitions?!  thx - ph

---

### Post by vincente on 2006-06-26
[QUOTE=jasutton]A swap partition is the same idea as the pagefile in window$.  That is, it's a piece of the hard drive that the OS can use as memory if it needs a little extra.  It's generally desirable for the OS to use physical memory (RAM) as much possible, but sometimes your computer needs more memory then it actually has.

I would recommend moving the data you have off to another location (the first hard drive would be good if you have room on it) and let the install re-partition the drive automatically.[/QUOTE]

At first, i thought the swap partition is only needed during the installation. Thanks for your inputs.

And yes i have move the data to the first hard drive and let the installer repartition the drive automatically. 

I would say installation is pretty smooth.

---

### Post by JazzSax on 2006-06-27
[QUOTE=gobot] Interface is not intuitive for me - anyone seen installation docs regarding existing partitions?!  thx - ph[/QUOTE]

I am experiencing the same type of issues. I originally had Ubuntu Dapper installed, but wanted to give SuSe 10 a whirl. Tried to come back to Dapper with new CD, but only shows my HD as one big unallocated space. The original CD I had did not have the LiveCD Boot/Install thing that they added, and it saw ALL of my partitions and would automatically set up / and swap partitions to the partition I desiginated. This new partitioner in the installer keeps giving me errors and will not install...claiming no root file system found. I even set up and ext3 and swap partition manually and it still would not take. I suppose I could pull out the old CD and install followed by an apt-dist upgrade, but I am curious as to why all the issues and difficulty. Thanks  ](*,)

---

