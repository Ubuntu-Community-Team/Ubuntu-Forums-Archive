---
title: "wireless connection keeps freezing"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bolex100 on 2009-10-10
I Just changed my Wireless router from a Linksys. to a Belkin vision N1. My wife's Tosiba Qosmio used to have connection drop-out problems with the Linksys.  Now with the Belkin, My Dell 1525 is suffering. 
The connection is apparently still up (so Wicd says), but there is no data tranfer.  I can get back in if I disconnect/reconnect.

Any suggestions?

---

### Post by coffeeaddict22 on 2009-10-11
Hi,
A good place to start looking might be your log files (System/Administration/log file viewer, or via the terminal in /var/log), especially the syslog file.
Have a look through the output of ```
sudo iwconfig
``` as well if nothing's obvious, and another thing worth doing would be to check with ```
sudo iwlist scan
``` to see if there's more than one network in your area on the same channel.  It's easy enough to change the channel on your router, and sometimes that stops crosstalk.

---

