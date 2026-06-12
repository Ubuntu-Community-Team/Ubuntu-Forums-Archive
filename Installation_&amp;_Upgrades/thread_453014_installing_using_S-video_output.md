---
title: "installing using S-video output"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by dcorwin822 on 2007-05-23
Hi, i have a old Dell GX100 i got for free(733Mhz,256meg,80gig Hdd,10/100 Ethernet). I put in a Radeon 7000 PCI video card and i connected it to my TV thru S-Video.   How can I install Ubuntu onto that system when X complains it cant find a screen? attaching a reg monitor would be a real pain in the *** so i'd like to be able to install using S-Video. Thanks for the help!

---

### Post by jocko on 2007-05-24
Unfortunately the xorg drivers for ati cards does not support tvout, so I think the only way is to connect a monitor.
But if you get tv output before xorg loads I think it's possible to get an alternate install cd or dvd and do a textmode install.
Another problem with your graphics card is that ati's proprietary drivers does not support it.
The gatos project have a patch that adds tvout to the xorg drivers, so it is possible to get it working if you know your way around the command line.

---

