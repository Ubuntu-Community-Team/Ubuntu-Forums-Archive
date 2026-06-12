---
title: "Intallation debugging (freezes at 94%)?"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by njparton on 2007-12-19
Now that I have Gutsy (AMD64) running successfully as my NAS device, I want to install it on my desktop PC.

I've tried this twice but the installation locks my PC up at 94% complete both times. System completely freezes and I have to power it off.

How do I debug this to find out what is the offending hardware? Live CD seems to work fine.

Specs for my PC below:

EVGA 680i MB (P30 BIOS) (onboard sound and RAID switched off)
Q6600
4GB PC6400 RAM
nVidia 8800 GTS 640
X-Fi Xtrememusic soundcard
160 GB WD PATA HDD (other hard drives containing windows etc unplugged).

Any ideas anyone?

---

### Post by KenRoberts on 2007-12-19
Are you sure it is really frozen, and not just extraordinarily slow? First time I installed 7.10 there was a network cable plugged in, to firewall, and I configured network - but firewall was set to deny all attempted traffic from the new Ubuntu system.  There were some long pauses - which I assume were attempts to communicate eg with a name server, but each such attempt had to time out.  Anyway, all went thru in about an hour.

Second time I did 7.10 install, network cable was not plugged in, and network config was deferred to later time.  There were not such long pauses during the installation.  With a laptop you might have to go into bios to disable wireless network?  Not sure how that is.

---

### Post by njparton on 2007-12-19
Dead as a dodo, not just slow.

Anyone got any other ideas?

---

