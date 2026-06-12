---
title: "System slow, apps drop out since upgrade"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by pappo on 2007-03-14
I installed Ubuntu 6.10 and it was all fine until I upgraded the 140 packages it said I needed.

At first the network quit working and I had to edit /etc/network/interfaces and move my ath0 (wireless card) to the top of the file, because it was trying to use my eth0 (wired connection) which is not connected.  After moving ath0 I was able to get back to the network.......I guess you can figure that out since I am posting this....LOL

I try to select Applications-->Accessories-->Terminal and the bar shows "Starting Terminal" but it never starts.

I have the applet for System monitor and when I select that, the same thing happens.  It tries to start it but then dies.


Regards

Pappo

---

### Post by pappo on 2007-03-14
Additional data.

I can bring up Firefox and Thunderbird from the panel, but when I try to bring up a terminal, which is right next to Firefox on the panel, it does not finish.

I checked /var/log/messages ,  Xorg.0.log, and user.log and I don't see any error messages pertaining to terminal not being able to load.

---

