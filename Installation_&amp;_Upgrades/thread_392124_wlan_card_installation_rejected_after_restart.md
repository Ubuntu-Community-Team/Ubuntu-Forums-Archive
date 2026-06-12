---
title: "wlan card installation rejected after restart"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by madgyver on 2007-03-24
hi @ all, ive got a problem with my wlan card installation.

i already tried to install the Ralink rt2661 card as the "Howto on Edgy Eft with Wpa..." describes bout it wont work either....

i have a pIV 3,6Ghz; nvidia 6800gt and 1gig ram running Ubuntu Edgy 6.10. The driver i used 4 the wlan card is from serialmonkey the rt61-cvs driver. after the first install (not like the howto says - just make and make install) the driver works perfect installing and configuring dont make any problems at all and i have inet connection too. but after restart the driver is missing and i cant get it to run twice. the network manager shows wmaster0 and wlan0 like @ the install of ubuntu where the setup programm has detected a rt2600 card. but this driver wont work.

after that i tried out the howto in this forum and i could get upto step nr.9 but when i type iwconfig and press enter the system hang up and wont start again. not common neither in recovery mode. in recovery mode the console shows: "BUG: soft lockup detected on CPU#0"

i dont know whats wrong is it the driver? but why should this be? the driver has worked perfectly first time.....

thank 4 any help :confused:

---

### Post by madgyver on 2007-03-24
ive just tried the original ralink driver 4 rt61 cards but now iwconfig shows "no wireless extension"...

---

