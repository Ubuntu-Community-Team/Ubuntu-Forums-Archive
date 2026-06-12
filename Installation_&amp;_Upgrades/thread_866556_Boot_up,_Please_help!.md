---
title: "Boot up, Please help!"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by wills1 on 2008-07-21
I used this tool to format my hdd [http://dban.sourceforge.net/](http://dban.sourceforge.net/) 
I had a pirate copy of windows installed. And I am selling the computer so decided to format the hdd and install ubuntu, But having problems. Used dban, Autonuked
	rebooted the system with the ubuntu cd in. Ubuntu menu comes up. I have tried installing, and running off the cd. It comes up with the ubuntu screen like its loading. Then just goes to a black screen which says: Busybox v1.1.3 (Deban 1:1.1.3-5ubuntu12) built in shell (ash)

When the ubuntu screen comes up when its
	installing, or trying to run off the cd. The floppy drive lights up. Then it just goes to the screen I just mentioned 

Now Im worried I've messed up the computer.
Any help would be fantastic :)

---

### Post by upchucky on 2008-07-21
old mbr is corrupt, repartition the drive then try again, gparted will fix it.

---

### Post by wills1 on 2008-07-21
> **upchucky said:**
> old mbr is corrupt, repartition the drive then try again, gparted will fix it.

Sorry but could you explain how to do that?

---

### Post by upchucky on 2008-07-22
get gparted use it to partition the drive, install Linux

if it is stopping during the install, or the live cd boot then it is probably choking on the monitor, you will need to know the monitor specs to do the install

if you get no progress with ubuntu live cd, then get KNOPPIX it should boot from cd then you can get monitor settings from the messages it shows you

---

