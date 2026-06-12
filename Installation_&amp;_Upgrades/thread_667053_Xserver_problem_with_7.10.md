---
title: "Xserver problem with 7.10"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by dasan on 2008-01-14
I hav Upgraded my sysytem to
asus M2N MX-SE board with nvidia chipset 
athlon 4400 processer

When i put Ubuntu 7.10 Live cd to install  Xserver is not loading i can hear the loging in sound but the moniter siply blinks
Also i can get command prompt by pressing alt+ctrl+F1..
What to do ?
Ubuntu 7.04 is loading fine ..
please help

---

### Post by Partyboi2 on 2008-01-14
Go to the a terminal and reconfigure xserver
```
sudo dpkg-reconfigure xserver-xorg
```
Answer all the questons and if you are unsure choose the default answer.

---

