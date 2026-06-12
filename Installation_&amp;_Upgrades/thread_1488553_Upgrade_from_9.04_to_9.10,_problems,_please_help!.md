---
title: "Upgrade from 9.04 to 9.10, problems, please help!"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by dgrzalja on 2010-05-20
Hi. I have Fujitsu-Siemens Amilo M7400 laptop and had Ubuntu 9.04 installed, everything worked fine, i use this laptop for web development.. Used Gnome, and KDE on some occasions..

Yesterday Ubuntu asked me if i want to upgrade to 9.10 and i did, well bad choice i guess..

If i boot in default kernel 2.6.31-21-generic i only get up to login screen after which my laptop freezes.. 

If i boot 2.6.28-18-generic kernel i can log in to Gnome, but i don't see any mouse pointer, but mouse works because i see icons highlighting as i mouse over them, just no mouse cursor..

I then started KDE, and i can see mouse cursor there but no wireless network which works in Gnome..

I  don't know where to even start repairing, i'm a linux amateur, so i need your help.. 

I have to fix my laptop because i need to continue my work, so this is urgent..

Please help.. Thanks..

---

### Post by lemming465 on 2010-05-21
In general if you need to downgrade, you are looking at a reinstall; upgrades in Ubuntu are one-way trips.

Because of the amount of churn in the X-window / kernel situation currently, I like to test with live CD's to very all my hardware still works *before* allowing upgrades.  A suggestion for next time.

Does the text-mode login work?  E.g. if you press CTRL-ALT-F1 then Enter, do you get a prompt "login:"?  If so, you might want to try:```
sudo -i
apt-get update
apt-get upgrade --fix-broken
dpkg-reconfigure xserver-xorg
```
That might or might not improve things any.

Another possibility is to try moving to 10.04 "lucid lynx"; that has another 6 months of video development behind it.

---

