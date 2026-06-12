---
title: "installation crashes and can not recover"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by shreko on 2005-07-05
I have had some serious issues with my machine, and I can not figure out what is going on. First little bit of history: initially dual boot, w2k and knoppix 3.3 on HD. Then, few months ago I installed PCLinuxOS and started crashing. Then I tried Mepis, same thing, Finally, I settled on Ubuntu Hoary and still problems. I even removed windows partition and iti is fully linux now. I've installed Ubuntu over and over 4-5 times in last few days. Installation goes smooth, everything works for few hours and then, shuts down itself. Or I had few cases when machine freezes, I reset and then can not recover. 
Here is the screen output of the latest boot sequence:
Staring Ubuntu
pivot-root: No such file or directory
/sbin/init: 428: cannot open dev/console No such file
Kernel panic-not syncing: Attempted to kill init
   and stays there hanging forever.

Other time hangs on starting hotplug

Thanks,

Shreko

---

### Post by jasmuz on 2005-07-05
[QUOTE=shreko]I have had some serious issues with my machine, and I can not figure out what is going on. First little bit of history: initially dual boot, w2k and knoppix 3.3 on HD. Then, few months ago I installed PCLinuxOS and started crashing. Then I tried Mepis, same thing, Finally, I settled on Ubuntu Hoary and still problems. I even removed windows partition and iti is fully linux now. I've installed Ubuntu over and over 4-5 times in last few days. Installation goes smooth, everything works for few hours and then, shuts down itself. Or I had few cases when machine freezes, I reset and then can not recover. 
Here is the screen output of the latest boot sequence:
Staring Ubuntu
pivot-root: No such file or directory
/sbin/init: 428: cannot open dev/console No such file
Kernel panic-not syncing: Attempted to kill init
   and stays there hanging forever.

Other time hangs on starting hotplug

Thanks,

Shreko[/QUOTE]
 This is not a installation specific problem, you problem resides either in your mainboard or HD.
Try using another HD to install, if it works then replace the drive permanently.

---

