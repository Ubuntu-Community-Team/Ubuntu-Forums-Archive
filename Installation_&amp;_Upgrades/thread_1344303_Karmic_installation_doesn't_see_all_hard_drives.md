---
title: "Karmic installation doesn't see all hard drives"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by sites on 2009-12-02
So far I've installed Karmic on several computers and a couple of laptops without much trouble.  However, on two systems there's a problem i haven't been able to solve.  A Dell Optiplex 755 system with Hardy, and a custom pc with the X58 chipset that has Jaunty, both with a second hard drive for backups.  I always give /home a separate partition so each new install can be done clean without losing any files.  Basically, the OS drive has swap, root, and home partitions, and the second drive is there for backups only.  When installing Karmic on these two systems it doesn't recognize the OS drive at all.  It does offer to install on the second hard drive (sdb), but reports that there are no operating systems installed on the computer and doesn't even show the first drive (sda).  From a live environment I can see the drive is there in gparted, but it will not show up during an attempt to install.  I've tried every bios setting possible but no luck.

Is this the fault of grub 2 being used by Karmic instead of grub 1.5?  I didn't run into this problem on a few other systems, but these two are getting the best of me.  I can't find a solution to this anywhere online although i've noticed a few others have had the same problem.

---

### Post by sites on 2009-12-02
Just found a solution in post #15 of [this thread]("http://ubuntuforums.org/showthread.php?p=8429435#post8429435").

---

