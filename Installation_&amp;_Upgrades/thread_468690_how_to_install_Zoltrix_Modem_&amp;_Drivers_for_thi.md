---
title: "how to install Zoltrix Modem &amp; Drivers for this"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by Muhammad Ilyas on 2007-06-09
I want to use internet on Ubuntu, but it doesnt offer any dial-up application for conecting to internet.
Windows xp do hardware detection itself and install drivers also.
and setting up dial-up connection is too easier..
but i couldnt found any utility to do so in ubuntu..
please help me...
wat i ve done it is as follows:
1. install ubuntu
2. install Zoltrix Modem(hardware)
3. help me how to install drivers for modem.
3. help me how to set up dialup connection and how to use internet

---

### Post by ABCC on 2007-06-10
I think this ought to solve your problems:

[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

Drivers aren't really necessary, if all is well the linux kernel will include all the information necessary to run the modem. If I recall Zoltrix modems fall into the 'Rockwell' family of modems, which generally is supported by the linux kernel. You'll need a 'PPP' program to connect with dialup, where PPP = Point-to-Point Protocol. In gnome that's gnome-ppp, but there are plenty of other options available through Synaptic if that fails.

HTH,

ABCC

---

