---
title: "unable to install ubuntu because HD is &quot;Read only&quot; Asus EEE PC 900 unable to install!"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by xxxrichievxxx on 2010-12-31
Hello everyone! I have this problem, I tried installing Ubuntu 10.10 on my Asus Eee PC 900 netbook because my other installation was missing some operating system files. I'm using a usb for the ubuntu installation because the netbook has no optical drive. (I have no usb drive) i ran ubuntu from the usb and booted up live ubuntu without any problems. i ran the install ubuntu and about 2 minutes into the installation it says "Cannot copy/write files HD is read only" i pressed okay and it canceled the installation and rebooted automatically. i tried reinstalling the linux distribution that came with the Asus Eee PC 900 and that wouldnt install i get these errors:

[IMG]http://i55.tinypic.com/15yw0tl.jpg[/IMG] 

What can i do to install Ubuntu 10.10? if not, then the regular distribution?

thank you!

---

### Post by presence1960 on 2011-01-01
I am confused! You say you are using a live USB to install ubuntu but then you say you have no usb drive.

---

### Post by xxxrichievxxx on 2011-01-01
> **presence1960 said:**
> I am confused! You say you are using a live USB to install ubuntu but then you say you have no usb drive.

Oops my bad! I ment i do not have a usb dvd drive. thus why i am stuck using the usb method

---

### Post by presence1960 on 2011-01-01
You can format the disk from the Ubuntu Live USB using gparted. Boot the Live USB and use "try ubuntu without changes." When the desktop loads go System > Administration > GParted Partition Editor. Delete all existing partitions one at a time. Click Apply (green check mark) after each one. Please only delete one partition at a time. When the whole disk is grey and labelled "unallocated" you can continue to install Ubuntu. Select the use entire disk option.

_**[COLOR="Red"]I am assuming you already backed up any data you don't want to lose!![/COLOR]**_

---

### Post by xxxrichievxxx on 2011-01-01
> **presence1960 said:**
> You can format the disk from the Ubuntu Live USB using gparted. Boot the Live USB and use "try ubuntu without changes." When the desktop loads go System > Administration > GParted Partition Editor. Delete all existing partitions one at a time. Click Apply (green check mark) after each one. Please only delete one partition at a time. When the whole disk is grey and labelled "unallocated" you can continue to install Ubuntu. Select the use entire disk option.

_**[COLOR="Red"]I am assuming you already backed up any data you don't want to lose!![/COLOR]**_

okay i'll do this :D I'll keep you posted. I dont have anything on the net book so it's all good :) thank you!

---

### Post by xxxrichievxxx on 2011-01-01
> **xxxrichievxxx said:**
> okay i'll do this :D I'll keep you posted. I dont have anything on the net book so it's all good :) thank you!

Okay I used Gparted and i was able to create a partition from all of the allocated free space. then Gparted crashed and i decided to test and see if i could install Ubuntu. but i couldnt! i restarted and booted up dban and erased EVERYTHING && zeroed the free space, then tried the installation again and it worked! :D

Thnk you :)

---

