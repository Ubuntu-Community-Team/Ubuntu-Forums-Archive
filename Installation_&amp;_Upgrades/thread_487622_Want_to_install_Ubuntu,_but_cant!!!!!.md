---
title: "Want to install Ubuntu, but cant!!!!!"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by sa_ill on 2007-06-29
Hey 
Im using Windows Vista x86 on my Asus A8Js. I want to dual boot Vista and Ubuntu. 
My Laptop has a 120 GB hard disk with only one partition. 30GB is free in that partition. I wish to allot 20GB for Ubuntu.
I tried the shrink volume thing in Vista's Disk Management but it was only able to shrink it by 280MB.

What do I do?
I basically want to creat a separate 20GB or 15GB partition so I can install Ubuntu in that.

Help!!!!!

---

### Post by ThrobbingBrain66 on 2007-06-29
You can partition your disk using the Ubuntu LiveCD.  After you click the install icon and answer a few questions, it'll allow you to partition your hard drive any way you wish.

---

### Post by sa_ill on 2007-06-29
Ive tried that it doesnt work!!

---

### Post by daynah on 2007-06-29
He's right. When you put in the live cd to do this, it just says... no. I was told that this is because Vista uses a different type of NTFS?

I'm currently also dealing with this problem, but since it's with a new laptop, and I knew about the problem, I'm prepared to just reinstall Vista in a partition of whatever size I want.

sa_ill, I understand that if you have a lot of important settings on Vista, this could be painful. But the only solution I've found for myself is to reformat my computer and reinstall Vista. During the process of Vista there's apparently an advanced install where you can partition in for only 20 gb min (I'm doing it for 30 gigs because I wont be using it often, but I will be putting WoW on it). But the last time I installed Vista, it took four hours. If you can do that, for example, if it's a new computer like mine that you haven't done much with, then don't work too much more with it. :) If you can't, just say so and I'll also eagerly wait for someone to come up with a better plan!

For the record, my Asus W7S gives me a xorg error about not having a screen. Does your Asus give you this error or is the Vista problem the only thing?

---

### Post by sa_ill on 2007-06-29
> **daynah said:**
> He's right. When you put in the live cd to do this, it just says... no. I was told that this is because Vista uses a different type of NTFS?

I'm currently also dealing with this problem, but since it's with a new laptop, and I knew about the problem, I'm prepared to just reinstall Vista in a partition of whatever size I want.

sa_ill, I understand that if you have a lot of important settings on Vista, this could be painful. But the only solution I've found for myself is to reformat my computer and reinstall Vista. During the process of Vista there's apparently an advanced install where you can partition in for only 20 gb min (I'm doing it for 30 gigs because I wont be using it often, but I will be putting WoW on it). But the last time I installed Vista, it took four hours. If you can do that, for example, if it's a new computer like mine that you haven't done much with, then don't work too much more with it. :) If you can't, just say so and I'll also eagerly wait for someone to come up with a better plan!

For the record, my Asus W7S gives me a xorg error about not having a screen. Does your Asus give you this error or is the Vista problem the only thing?


No my Asus has never given me that error. But there are many funny things that happen to the display, like resolution change outta nowwhere, sumtimes i cant set the brightness more than 25%.
Coming back to the topic, will GParted help??

---

### Post by into_311 on 2007-06-29
There is a live cd version of Gparted you can download. It aims to be a free/open-source Partition Magic clone.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I've had very good luck in working with my NTFS partitions on machines. However, I haven't tested it with vista. But they come out with a new release several times a month.

---

### Post by sa_ill on 2007-06-29
yeah I tried that same problem

Someone advised me of using Wubi? Is it worth??

---

### Post by stchman on 2007-06-29
> **sa_ill said:**
> Hey 
Im using Windows Vista x86 on my Asus A8Js. I want to dual boot Vista and Ubuntu. 
My Laptop has a 120 GB hard disk with only one partition. 30GB is free in that partition. I wish to allot 20GB for Ubuntu.
I tried the shrink volume thing in Vista's Disk Management but it was only able to shrink it by 280MB.

What do I do?
I basically want to creat a separate 20GB or 15GB partition so I can install Ubuntu in that.

Help!!!!!

Run a chkdsk /f and a defrag.  Once this is done you should be able to shrink the volume to a much smaller size.

---

### Post by sa_ill on 2007-06-29
> **stchman said:**
> Run a chkdsk /f and a defrag.  Once this is done you should be able to shrink the volume to a much smaller size.

OK Boss Ill try that!!!

---

