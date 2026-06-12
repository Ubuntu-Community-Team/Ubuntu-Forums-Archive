---
title: "Problem during install"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Ataxia on 2011-06-13
hi there 

I've been trying to install Ubuntu alongside my win 7 but have been coming across a problem with the partitions.

When it comes to the allocate drive space the space it allocates seems extremely small.
It allocates as follows

SDA1 Fat32 104mb 33mb used
SDA2            134mb unknown
SDA3 NTFS 790248mb 239528mb used
free space 209715mb

The free space is from a windows partition that I shrunk to allow space for Ubuntu

Now I am confused here should I be allocating more room to each of these partitions or selecting the free space??? When I select the free space it says no root system is defined.

Ive done an install previously but I don't remember having this choice before, so any help would be most appreciated.

---

### Post by kc1di on 2011-06-13
Hi Ataxia,

there are a couple ways you can go.  there should have been a choice when you started the install a screen that asks you where you want to install Ubuntu one of the options was install alongside windows. and it would have partitioned the drive for you.

Given that you have already partitioned the drive I would allocate it as follows from the free space. you do that by checking the box during the partitioning  screen one of the options is do something else.  

It will bring you to a screen that list all your current partitions.
in that scree just double click on the one you want to modify. 
in this case the free space.  you will then be take to a screen that will allow you to set the new partion.  

I would partition it this way:
10 GB -- / (root)
2 GB -- Linux Swap
remander for -- /(home)

you will be asked to choice the file system type (Choose EXT4)
there is a box for format partition (check it)
there will be a box for what type of partition to choose click on it and click the one you want for that partition.  When done click on done and it will take you back to the partition screen give it a moment to redisplay and choose the next repeat the process until your satisfied that you have it the way you want and hit install.  

you may also want to take a look at the following web page which may be of help

[http://http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

**[COLOR="Red"]AS ALWAYS MAKE SURE YOU BACK UP ANY IMPORTANT DATA BEFORE PROCEEDING WITH THE INSTALL.[/COLOR]**

---

### Post by Ataxia on 2011-06-13
Thanks for the info much appreciated. I have now got Ubuntu Installled but it has left me with a ocuple of other questions.

I have this new fangled bios system with a n Intel 2500K n a p8p67 asus mboard. Somewhere along the line the grub boot loader seems to have been lost or corrupted. To get into windows I have to select windows boot from the new bios.

Also do I have to use this new menu system or is there a way to revert to the one in 10.10?

---

