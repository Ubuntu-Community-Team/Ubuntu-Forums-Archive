---
title: "Dual Screen with ATI Card in 11.10"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by oliwel on 2011-11-13
Hi All,

I upgraded my workstation from 10.10 to 11.10 and I am unable to get my Dual Screen to work. I have a ATI Fire 3700 with two Screens, 1920x1080 each. I used to run a virtual desktop spanning both screens, so 3840x1080 px. 
After the update, I am stuck with a mirror-screen on 1920x1080, when I try to enable the second display I get an error that the max supported resolution is 1920x1920. I tried to install the propriety amd driver and uise the catalyst control panel but I dont even get the checkbox for dual screen here (it shows both screens but the dropdown for mode selection is disabled).

Anybody can help out? 

Oliver

---

### Post by Mark Phelps on 2011-11-13
Hate to ask the obvious, but did you go into Display and UNCHECK the box for mirroring displays, first?

Once you do that, you should then be able to set each monitor separately.  I'm using dual monitors on an ATI HD 4290, using the open-source drivers, and that works fine.

Also, when Display opened, it had my small monitor on the left, large one on the right.  So I dragged the monitor picture in the diagram to the right -- so the large monitor is on the left, now.

Since the one on the left was considered monitor (1) -- its resolution was governing the whole setup, until I unchecked the mirror box.

---

### Post by oliwel on 2011-11-14
> **Mark Phelps said:**
> Hate to ask the obvious, but did you go into Display and UNCHECK the box for mirroring displays, first?


Yes I did, but as soon I want to apply it says that 3840px is too large. When I set the res down on each screen the dual monitor setup works (but a 22" with 960px wide is no fun). Meanwhile, I found a solution in another thread: [http://ubuntuforums.org/showthread.php?t=1748037](http://ubuntuforums.org/showthread.php?t=1748037) - I set the Virtual in xorg.conf and switched to the oss driver, now it works.

---

