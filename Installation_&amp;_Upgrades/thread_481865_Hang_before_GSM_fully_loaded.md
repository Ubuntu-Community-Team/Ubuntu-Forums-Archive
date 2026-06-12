---
title: "Hang before GSM fully loaded"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by supersaiyen on 2007-06-23
Hello, previously had edgy installed from alternate CD, did upgrade to feisty using apt-get, upon reboot system locked. Tried fresh install from feisty Live CD, had monitor refresh rate problem. Installed from alternate install cd, replaced xorg.conf with my previous one as well as installed nvidia-glx drivers. 

When booting just after splash get a black screen with a clockish cursor that i can move for about 1/2 a second then a full system freeze, even reset switch is funky and needs reset 2X. can boot into recovery mode and startx and gdm fine with the exception of failing to start HALd. tried noapci param to no avail. checked messages log, nothing seemingly suspicious. Any suggestions?

---

### Post by supersaiyen on 2007-06-23
Not sure why, but remembering some difficulty i had with edgy i remembered something about run-levels. I'm an old red-hat man, but to my knowledge ubuntu does not differentiate between runlevels 2-5, but i edited /etc/event.d/rc-default to runlevel 3 and all is working just peachy. Hope this helps some in the future, though im still not sure of the reasoning. If anyone worth more salt can lend some knowledge i would be grateful.

---

