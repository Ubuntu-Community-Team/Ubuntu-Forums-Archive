---
title: "Ubuntu overall impressions on different pc's"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by chrissk_2 on 2010-06-01
Hi all,

i recently installed ubuntu lucid 64 bit on 3 different configurations and i though of posting the results here for anyone to see.

First pc is an 24'' imac with intel core duo2 2.16Ghz and nvidia 7600 4gb ram.
Everything worked perfectly out of the box with no tweaking needed except for installing the nvidia and broadcom proprietary drivers. Also i did not install the firmware for the build-in camera but i don't really care about that. System boots in 14.5 secs in clean install and about 18-20 secs with compiz, cairo-dock etc, and suspends - resumes - hibernates perfectly. The only minor issue i noticed is that hibernate takes a lot of time, this can be improved. I also installed the 2.6.34 kernel with nouveau drivers and now i have 3d acceleration. However with this kernel suspend - hibernate no longer works, but since its not a normal procedure i don' t count this as an problem or bug.

Second pc was a dell (i don't remember the actual model) with dual core cpu and 2 gb ram and on-board intel graphic card. For some reason dmraid caused a lot of problems during the installation (it could not detect the partitions) but once i removed it everything worked perfectly. System is extremely fast and snappy, it boots in 15 - 17 secs in clean install and with compiz etc enabled. Suspend - resume - hibernate is perfect and extremely fast, especially resume with completes in a couple of secs. Everything works perfectly. The only minor annoyance is the terrible performance of the intel graphic card on compiz effects. OpenGL implementation is still lacking i suppose.

The final pc was a sony vaio f series laptop with 4 gb ram, intel i5 processor and nvidia 330. In this configuration i had some minor issues with the nouveau driver (could not correctly detect screen size) and the nvidia driver could not detect the monitor. I solved that by manually editing xorg.conf to add a EDID param and now everything works Ok. However during resume from suspend - hibernate the nvidia driver still can not detect the EDID so resume comes up with a black screen. Also i noticed a delay during boot for some unknown reason, probably something during partition detection from the kernel, not sure. Also during shutdown i get a small noise coming from the speaker as the sound card is turned off. This does not happen in 2.6.34 kernel i tried.

Overall this is the best ubuntu release to date for me. Hopefully someone will fix these minor issues especially with nouveau, so that we can get rid of the nvidia driver for good.

Thanks ubuntu devs

---

