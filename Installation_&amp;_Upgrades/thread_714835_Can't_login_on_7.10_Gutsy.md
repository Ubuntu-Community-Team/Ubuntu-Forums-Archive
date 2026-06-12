---
title: "Can't login on 7.10 Gutsy"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by Max Carey on 2008-03-04
Just upgraded to 7.10 Gutsy from 7.04 Feisty (which was an upgrade from my original version 6.10 Edgy). The upgrade/installation went through without any issues (I used the update manager). When I rebooted I ran into problems. When the login screen loads, it flashes briefly, then reloads a couple seconds later. It repeats this over and over for who knows how long. I'm thinking this might be a graphics card issue, but I'd like to get some ideas before I start messing around with things. I can access the command line through recovery mode. I'd really appreciate any help.

Pentium D 2.8GHz
512 MB DDR2 SDRAM
ATI Radeon X300 Graphics Card

---

### Post by taurus on 2008-03-04
See what happens if you reconfigure X again. 

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Max Carey on 2008-03-04
I ran dpkg-reconfigure with and without the -p option, messed around with my graphics card settings and screen resolution/refresh rate a bit, but still ran into the same problem. Could it be a driver issue?

---

### Post by Max Carey on 2008-03-05
Still haven't had any luck...tried installing fglrx driver but ran into issues, so uninstalled it and reconfigured xorg. Anybody have any ideas???

---

### Post by taurus on 2008-03-05
Which driver are you using when you reconfigured your X server?  Try using **vesa** driver to see if it gets X up and running again.

---

