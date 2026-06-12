---
title: "unable to satisfy all constraints on the partition"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by shushu on 2008-01-03
Trying to install new fresh install of ubuntu, and got that error.
Also got the error trying to partition VIA GParted.

I thought the issue is the HDD but I have succeeded to create fat system on that HDD.

What to do??

Thanks,
Oded

---

### Post by Pumalite on 2008-01-03
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by shushu on 2008-01-04
Hi,

Thanks for the quick reply, the issue is that I don't want a dual boot machine I want only an Ubuntu machine.
When try to install the Ubuntu and get to the partitioning part I selected one drive so it will erase all and install from scratch on all drive.
After the starting the install process and during the work it tells me that the creation of the partition failed with the message "unable to satisfy all constraints on the partition".
When tried to do it manualy after the install failed from the GParted I get a message telling me that /dev/sda1 no such file or directory

:confused:

---

### Post by Pumalite on 2008-01-04
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it, delete everything in your drive. Then make a new large partition of your whole hard drive, format it ext3 if you want. Then install Ubuntu.

---

### Post by kobor42 on 2008-04-02
Well, I would like to ask you, that if you begin to solve the problem then just take it serious, or else stfu.

I just created all my partitions for ubuntu with gparted, one for boot, root, home and swap. I resized the things to save my datas from my gentoo I had previously. Gparted did everything all right, but it freezed everytime it had to requery the partiton table after the changes. Ok, that's a bug I can live with.

But it mixed the order of sda-s, so I launched fdisk. and fixed the ordering. relaunch gparted and can't see anything. Launch parted, try to list partitions, and 

"Unable to satisfy all constraints on the partition"

Error is given back. But! I can see every partition in fdisk, I can see them even through /dev/sdaX, and can mount them; everything is there as it should be.

But neither the ubuntu installer, nor gparted/parted cant do anything with it.

Let me just say, that the style of your two reply-s, givin' a **** on the problem of shushu's pissed me off a lot. There is an error message and all you do is link in some pages which has nothing to do with the problem he found.

---

### Post by louieb on 2008-04-03
> **kobor42 said:**
> Well, I would like to ask you, that if you begin to solve the problem then just take it serious,...

Nice 1st post. You look like a forum troll to me.

And now to the OP:
The thing about GParted and the Ubuntu live CD installer is if there is something odd about the partition table (overlapping partitions or a primary partition inside the extended partition)  GParted will not try to work around it - it will just unt-uh and won't do any thing. 

fdisk or Disk Drake aren't picky they will do what ever you tell them to do,  even if it makes no sense. 
You have a couple of options - If theres nothing on the disk you want to try and save give cfdisk a try. its a little friendlier that fdisk.
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018")

---

