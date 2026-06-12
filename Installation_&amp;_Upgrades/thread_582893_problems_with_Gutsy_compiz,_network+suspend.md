---
title: "problems with Gutsy: compiz, network+suspend"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dede54 on 2007-10-20
Hi List, I am new Ubuntu user. I installed 7.10 on my thinkpad z60m - no problem. However:
1) I cannot use compiz ( I have ati  card) (message Desktop effects could not be enabled)
2) suspend works but after suspend nm eat more 90% cpu and I cannot restart network. 
Earlier, with 7.04 I had not such problems,  
Maybe somebody solved  already these problem?
-ajm

---

### Post by brujoand on 2007-10-21
I have the same problem with suspend, I made a little script to restart nm that might help you out though.


#!/bin/bash
sudo killall -KILL NetworkManager
sleep 1
sudo dbus-launch NetworkManager

---

### Post by miobio on 2007-10-24
Same problem here with suspend (not interested in XGL for now :-D )!

In Feisty, I had to unload some modules before suspend, can that be the reason?


How can I remove modules before suspendin Gusty?

Also, the battery thing on top doesn't work, it shows me as plugged in all the time :-(


HEEEELP!!!

---

