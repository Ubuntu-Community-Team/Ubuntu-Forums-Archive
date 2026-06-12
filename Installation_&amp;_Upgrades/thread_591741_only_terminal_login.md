---
title: "only terminal login"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by wolvish on 2007-10-25
I'm kinda new to Ubuntu, just upgraded to gutsy from feisty. When I tried to boot all I got was something like "device-mapper: table: 245:1: linear: dm-linear: device lookup failed". I searched for the error in the forums and found other people that had the same problem of course, the code that it said to enter was "sudo aptitude remove evms" which I tried in recovery mode. When I rebooted it went through the loading screen, but then just gave me a terminal-type login. I don't know how to get to the graphical interface.

---

### Post by wolvish on 2007-10-25
Found the solution... Had to configure the xserver. For anyone with the same problem, 
sudo dpkg-configure xserver-xorg

---

