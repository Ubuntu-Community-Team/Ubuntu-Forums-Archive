---
title: "Ubuntu Installation"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by Drawstop on 2007-01-08
Am running a Pentium D 3.40 with three SATA drives.  XP is on the C drive and I would like to install Ubuntu on one of the other SATA's.  There is loads of free space.  Will Ubuntu give me the choice of any of the three drives for the install?  I HATE windows but have to use it as I cannot locate a scanner that Ubuntu will drive.  Any help will be most appreciated.  Regards to all. Drawstop.

---

### Post by az on 2007-01-08
> **Drawstop said:**
>   Will Ubuntu give me the choice of any of the three drives for the install? 

Yes, it should.  The default option it offers may not be the one you want, but you should be able to do it.  You should also be able to do it by hand.

If you run the Ubuntu installer and don't see the option to automagically resize and use the freed space from one of your drives, you can always use the manual partitioning step to shrink an existing partition on the drive you want to use and that will create the free space.  Then, go back and the default option should be to use that free space.

---

### Post by goodfella on 2007-01-08
You also might want to try this link [dualboot instructions]("http://www.ubuntuforums.org/showthread.php?t=179902") it details how to setup windows and ubuntu on seperate drives.  I used it myself and have ubuntu on one drive and windows on another.  I use grub to load either windows on ubuntu and if my ubuntu install goes down (not likely to happen) I just set my windows drive to the first bootable hard drive in my bios and windows boots normally.

---

