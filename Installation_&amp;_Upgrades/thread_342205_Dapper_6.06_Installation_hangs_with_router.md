---
title: "Dapper 6.06 Installation hangs with router"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by YumaJim on 2007-01-19
Problem 1:
On my home network, I have several computers connected via a LinkSys Wireless router.
The router does not have a broadband Internet connection.
When trying to install any of the 6.06 or 6.10 (live CD) Desktop systems, the install process would hang
when looking for the Internet connection. There is none at that time because I use a dialup
modem connected to the system I'm doing the install on.
This problem was solved by disconnecting the ethernet cable to the router before starting the installation.

Problem 2:
Because this system uses an old CRT Monitor, that the installation software can not communicate with,
 the monitor is set to a very low screen res., like 600X480, by the install program. With such a very low screen resolution
it was very hard to do the installation ( to get to the various buttons ). I finally did get the
install completed and then edited X11.conf to add the correct Horz and Vert parameters.

This remains a problem. My suggestion would be for the install program to default to a higher
screen resolution since the install screen decorations are designed for a higher screen resolution. -- YumaJim

---

### Post by wpshooter on 2007-01-19
Why don't you use the ALTERNATE (text based) CD to do the install, so you can choose the resolutions that your card and monitor are capable of during the installation process ?

---

