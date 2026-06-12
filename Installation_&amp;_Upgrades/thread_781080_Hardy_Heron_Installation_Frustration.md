---
title: "Hardy Heron Installation Frustration"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by marksoccer on 2008-05-04
I have been trying to get my brother's computer setup with a fresh install of Hardy Heron all day and cannot seem to figure it out.  Long story short, I know the disc is not the problem, because I installed it fine on my parent's computer.  The problem is that when I go to install via the install option at the boot screen or via the install icon once the live cd is booted, the installation goes through to 100%, but then loads the live desktop rather than asking me to restart and load ubuntu from the hd.  When I restart, it says grub 1.5 is loading and then says ERROR 15.  Then I booted into the live cd and went into grub and tried "find /boot/grub/stage1" and it did not find anything.  Since I know where it installed it, I tried manually "root (hd1,0)" and then setup hd0 (also tried hd1)... which then said that no stage1 was found.  I tried some suggestions from other forum posts that said I should mount the installation and then use grub which also did not work.  I then tried to find menu.lst and found that it is not there.  I don't know what to do and I cannot figure out why the install boots into the live cd instead of asking for a restart.  I have tried multiple installations with multiple options (manual and guided largest continuous space).

System Specs:
Athlon XP 2500+
ATI AIW x800 XT
SOYO Socket A Motherboard
512mb DDR RAM

---

### Post by Patb on 2008-05-04
Mark, you've probably already tried this but [this thread]("http://ubuntuforums.org/showthread.php?t=24113") might help.

Another thing, in grub, I think your first hard drive (and you seem to have only one) will be designated "hd0" not "hd1".

Hope this helps.  Cheers, Pat.

---

