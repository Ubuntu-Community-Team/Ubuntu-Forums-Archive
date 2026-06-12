---
title: "Gutsy fails to enter graphcs mode on install"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by pm124493 on 2007-10-19
Trying clean install of v7.10 i386 CD. Runs until it tries to load GUI and after nine failures errors out and says couldn't load GUI try again in two minutes.
ECS671T-M MB, 1GB PC6400, 80GB ATA HD, Onboard Mirage 3 video, GLAN etc. P4 640 3.2GHz.
I suspect it is having trouble loading a driver for the Mirage 3 onboard video. I tried F4 option and setting to lowest 640x480x16. Still no go.
Any suggestions would be appreciated.
Thank you.

---

### Post by pm124493 on 2007-10-20
UBUNTU for some reason sets the Horz and Vert rates as 50-80H and 50-160V for this LCD monitor. The monitor was out of range. I did Ctrl-Alt-F1 and modified xorg.conf and changed the rates. That got X working on the monitor. After installation I had to went back to console and modify xorg.conf again to fix X. After that it works fine.

Question: Is there no accelerated driver for Mirage 3?

TIA:)

---

