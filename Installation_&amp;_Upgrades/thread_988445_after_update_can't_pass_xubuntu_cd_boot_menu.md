---
title: "after update can't pass xubuntu cd boot menu"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by gry on 2008-11-20
[my first ubuntu experience]
I burned xubuntu 8.10 cd on laptop.  Used cd to install 8.10 on desktop successfully.  A couple of days of moderate use later, a window pops up offering software updates.  I type my password, select something like 'all', it grinds for a while, then says I should reboot.  On reboot I get an error very early: "kernel panic-not syncing: attempted to kill the idle task" and hang until hardware reset (can't scroll back to see earlier errors).  Same thing happens with 'recovery mode' boot.  memtest86 from grub menu works fine.  

OK, I'll just reinstall: but no!  Now when I boot up from cd, I get the usual xubuntu graphic menu: Try xubuntu, install xubuntu, check cd for defects, test memory, boot from first hard disk.  But *any* choice pops up a window like:
[CODE]
Boot loader
live (or 'live-install', or 'check', or 'memtest', or 'hd')
OK
[CODE]
and hitting return gets me back to the menu. I would like to retain data from second disk, and from home directory.  How can I get past this?

[hardware: desktop 700MHz athlon, 500MB ram, two ide disks(previously SuSE linux), Soyo MBd, award bios]

---

