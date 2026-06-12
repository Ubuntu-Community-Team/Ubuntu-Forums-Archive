---
title: "Trouble partitioning for 7.10 installation"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Uberuntu on 2007-11-16
Hi everyone, this is my first post in this forum. Ok, so I finally had enough of windows altogether. I just went through 2 weeks of formatting a doing clean installs of XP and its still messing up so I've finally decided to try out Linux and see what all the buzz is about. First off I downloaded the Ubuntu .ISO and put it on a disk. I aslo did the same for gparted. So I restarted the system and booted gparted and formated so there was nothing but unallocated space. Then I booted ubuntu and used the install. Now heres the problem, I get as far as the 'parition hardrive' section, and there is nothing to choose from. I have used gparted a handful of times since then trying different types of partitions but to no avail. If I am not doing something correctly please let me know. Thanks!

---

### Post by rsambuca on 2007-11-16
There should be a selection to do Automatic partitioning, manual partitioning, or something like Use the entire drive.  What do you mean "nothing to choose from"?

---

### Post by Uberuntu on 2007-11-16
what i mean is when you get to that part of the installation, the options field is blank. When i have my external hardrive plugged in it works and i get those options, but it doesnt detect my regular internal. On the other hand when i first log on to ubuntu and i go to the system/admin/ (i think thats it) partition editor program. it detects my HD there but when i press the new button i get an error message and it crashes on me.

---

### Post by rsambuca on 2007-11-16
Strange.  If the gParted CD is seeing the drive, format the drive as ext3, and then Ubuntu should see it.

---

