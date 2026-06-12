---
title: "[SOLVED] Ubuntu forgets my network settings after reboot"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by TBTsjG89 on 2008-10-05
I'm using Ubuntu 8.10 and every time I start my PC I have to set my network settings, otherwise Ubuntu loads its default values (dhcp). I'm part of a LAN, and I have a static IP, no dhcp.
I have tried editing the /etc/network/interfaces file, but its content does not even correlate with the settings I manually type in the GUI window.
This problem didn't occur before I upgraded my system from 8.04.1 TLS

thank you for your help in advance

mr_krey

---

### Post by TBTsjG89 on 2008-10-05
I managed to solve the problem after an hour of googling. When you set your network settings, you **must** check the checkbox 'System setting'. For some reason it is unchecked by default. Doing this is necessary to make NetworkManager create a profile in /etc/NetworkManager/system-connections/, which will be loaded in the future.
I've attached a screenshot (scr.png) to my reply, so you can see what I mean.
Hope this will help somebody!

mr_krey

---

