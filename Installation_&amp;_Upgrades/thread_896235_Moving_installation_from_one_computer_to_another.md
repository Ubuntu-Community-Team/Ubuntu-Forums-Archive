---
title: "Moving installation from one computer to another"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by CyrusComputers on 2008-08-21
I want to move my installation of Ubuntu 8.04.1 from a 40GB drive on one machine to a much larger one on a different machine. Ubuntu will be sharing space on the larget drive with an alread-installed Windows XP. Both machines are P4, but with different chipsets. Is the move as simple as transering the contents of the ext3 on the first drive no a new one on the other, or are there more complex procedures involved? Also, once I move the files how should I install grub on the new drive without messing up my windows install? Thank you very much for any help.

---

### Post by RedPandaFox on 2008-08-21
I also would like to know this, I have Ubuntu on my PC with setting and everything I want to keep but I want it onto my new Asus laptop as I'm getting rid of my PC as of saturday.

It took me hours to get Counter Strike working under WINE and still be able to play online, I don't want to go thou that again!

---

### Post by SkonesMickLoud on 2008-08-21
Try this thread:

[http://ubuntuforums.org/showthread.php?t=599599](http://ubuntuforums.org/showthread.php?t=599599)

---

### Post by CyrusComputers on 2008-08-21
Thank you for that link. I have two more questions. First, from the Ubuntu cli how do I display the partition structure? Second, once I copy the partitions to my new hard disk, I plan to use GParted to increase the partition sizes. What would be a good size for the swap partition on a drive with 320GB available?

---

### Post by fourthofjuly on 2008-08-21
> **CyrusComputers said:**
> Thank you for that link. I have two more questions. First, from the Ubuntu cli how do I display the partition structure? Second, once I copy the partitions to my new hard disk, I plan to use GParted to increase the partition sizes. What would be a good size for the swap partition on a drive with 320GB available?
1) sudo fdisk -l
(-l is lowercase L, not one)

2) setting swap is not related to your HDD, ideally you should keep swap twice the size of your RAM

cheers!

devang.

---

### Post by SkonesMickLoud on 2008-08-21
> **CyrusComputers said:**
> Thank you for that link. I have two more questions. First, from the Ubuntu cli how do I display the partition structure? Second, once I copy the partitions to my new hard disk, I plan to use GParted to increase the partition sizes. What would be a good size for the swap partition on a drive with 320GB available?

No problem.  Just be VERY VERY careful with "dd".  It's become known as "Data Destroyer" because if your syntax is off by one misplaced letter, number, -, or / you run the risk of losing everything.  Best thing to do it type it all out, review it, erase what you just typed, type it out again, review it, review it again, have someone else look at it, review it again, then hit enter.  

I would recommend shrinking your partitions before you run "dd" as dd doesn't just copy data, it also copies blank space.  Personally, I shrink the partition to about .5 to 1 Gb larger than where the data ends.  Copying a 5Gb partition will go a lot faster than copying a 30+Gb partition.  However, if you're doing something like copying an 8Gb partition with 5Gb's of data, just run dd as is.  And make sure both partitions (the "if" and the "of") are the ***_exact_*** same size.  Copying 5Gb into 10Gb will cause you problems!  You can grow partitions later if you need to.

As for viewing the partition structure, you can either use a GParted LiveCD, or the Ubuntu LiveCD, which has GParted (albeit a less functional version) on it.

As for swap space, it's not dependent on HDD space.  If you have 2+ Gb's of RAM, you probably don't need any swap space.  However, if you want to use hibernate and/or suspend you will need to at least match your RAM.

---

