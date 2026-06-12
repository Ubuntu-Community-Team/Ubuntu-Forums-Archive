---
title: "pppoeconf success...then failure!"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2008-11-09
Hi all,
I installed 8.10 this morning on a computer at work (by the way, it instantly recognized the audio, display and ethernet devices in a way that a week of fighting with XP didn't!). When I first ran a live CD session, Ubuntu, through pppoe, successfully accessed my DSL connection. 
After installing the OS, however, pppoeconf fails to create a ppp0 and ifconfig ppp0 returns: 
"error fetching interface information: device not found"
Any ideas?
David

---

### Post by dbclinton on 2008-11-10
I've got some new wrinkles on this mystery:
During a live cd session, Ubuntu recognizes my DSL automatically on interface eth0. But when I log on to my installed Ubuntu, not only is there no real eth0 interface (just something called ifupdown(eth0)) but there's no MAC address either. Also, when I go into Network Manager (even using sudo) on the installed Ubuntu, I'm not allowed to add a new interface or edit the existing one ("no new connecdtions allowed").
What's wrong with it?
Thanks

---

