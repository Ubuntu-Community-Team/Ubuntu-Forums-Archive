---
title: "NIC no longer works after install"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by omishan on 2010-12-08
I installed ubuntu today, and now the nic no longer works in windows or ubuntu

in windows it keeps going from network cable unplugged to identifying

in ubuntu it just reads as network cable unplugged

network cables are fine, modem is good, i connected modem to a cisco switch and it comes up, i connect my pc to the switch and the interface doesnt light up

network card was fine until i installed ubuntu, i downloaded it, installed it, now nic is no longer working.

its a realtec interface built in to a asus motherboard, any ideas how this is fixed?

---

### Post by omishan on 2010-12-08
found a solution that worked.

Boot on windows.
Go to the device manager and get into "properties" for your network card.
In the "Advanced Options" tab select:

Wake-on-lan after shutdown | enable

Reboot into linux. Your network card should be working.


//stupid windows!

---

