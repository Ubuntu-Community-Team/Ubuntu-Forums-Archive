---
title: "reinstall ubuntu on a crashed ubuntu/xp daul boot."
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by GraeSquirrel on 2008-01-08
I had installed Ubuntu in dual boot form with XP.

Xp crashed on me even before splitting out to the Ubuntu OS.  Unfortunately I lost the reinstall disk for XP so I'm SOL and figuring its the best time to get rid of windows altogether.

Ive got the Ubuntu install disk but haven't been able to get the Ubuntu to reinstalled through the currently installed boot software.

What is the best way to handle this?  Would using grub help here? do I need to get windows reinstalled just to reistall Ubuntu over it destroying it?:confused:

---

### Post by benrboone on 2008-01-08
Lets make sure we are on the same page

first you plan to delete your xp image
second you wish to expand your gusty image to use the complete drive
is this correct?

---

### Post by stump138 on 2008-01-08
when you assign your partitions and use the partition tools on the live cd, just tell it to use the entire disk.

If you are having problems with the live cd, consider switching over to the alternate install cd.  available [here]("http://www.ubuntu.com/getubuntu/download")

just check the box that says you want the alt cd.  

Good luck!

---

### Post by GraeSquirrel on 2008-01-08
Yes  benrboone that is correct.  Used the ubuntu about 95% of the time.

---

### Post by zvacet on 2008-01-08
Download [Gparted](http://gparted.sourceforge.net/) and you will be able to do what you are planing.

---

### Post by Gina on 2008-01-08
Yes GParted works a treat :)  You can increase or reduce partition sizes as well as create and delete partitions.  You can even extend partitions downward into free space and GParted will move everything down.  Easiest way to get it is with Synaptic Package Manager - search for it and install.  All so easy after many years of Windows!! :lol:

---

