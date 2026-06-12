---
title: "Can't boot Live CD (ATI graphics related)"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by kook44 on 2005-12-04
Hi-
Just got a new PC and want to get ubuntu up & running as soon as possible.  I have an ATI radeon x300 card, and a 24in dell 2405FPW monitor.  When trying to boot from the live CD, I get:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the the X server output to diagnose the problem?"

When I select "Yes", it just re-displays the error msg and hangs.  I know there are some issues with ATI cards, but I have no idea what to do.  I tried booting knoppix live CD.  It does boot into X, but I can't use my optimal resolution (1920x1200).

Will it be possible to get 1920x1200 in ubunto (or knoppix) with the ATI card?

Also- niether ubuntu live or knoppix can detect my onboard nic.  What do you have to do to use onboard nics?

---

### Post by kook44 on 2005-12-04
ok-
got it up & running.  At the "hanging" part - I had to hit ctrl+alt+F1 to get a terminal prompt.

then I edited /etc/X11/xorg.conf.  had to find the "device" section & change the Driver from "ati" to "radeon" 
Then, for the right resolution, I added "1920x1200" to each "Display" subsection.

typed "startx" and i was in biz.

now for that network card...

---

### Post by taurus on 2005-12-04
Do you know the brand of your onboard nic?  It's weird that ubuntu can't find it because it didn't have any problem finding it on my desktop and mycrappy HP laptop...

---

