---
title: "Edgy Live CD does not see partitions"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by beefon on 2007-03-31
Hello, i'm trying to install Ubuntu.. I did it before many times, but now live cd doesn't show me existing partitions. It says that my HDD is completely clean, but i have 4 ntfs partitions, one of then is primary.
And Alternative CD doesn't see partitions too. I don't know whats going on. 
I had installled Ubuntu 6.10, but then i removed it using Partiton Magic and want to reinstall it.
I also did "fixboot" and "fixmbr" in WinXP's repair console to repair standard XP bootloader.
I did it many times.. And Live CD was always able to find partitions, but no - nothing.
Can you help me?

---

### Post by beefon on 2007-04-14
Hey, please answer if you know what's going wrong!
I downloaded 7.04 beta Kubuntu CD, and it's installer does not see my existing partitions too.
But if i open System Preferences, and then Disks and FS, i _can_ see my partitions!
And fdisk -l /dev/hda shows my partitions too! 
Please help, maybe i have to repair my HDD somehow? What i should do? Check?

---

### Post by bulldog on 2007-04-14
PM isn't the right tool to use when you want a Linux partiton.
Try the free GParted live cd,it's similar with PM and has a GUI.
Download it and burn it to a cd-r and use the cd to boot from.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Maybe it will show your partitions as they should be.

---

### Post by beefon on 2007-04-14
GParted doesn't show me partitions too.
But Mandriva's P-P 2007 installer show!

---

