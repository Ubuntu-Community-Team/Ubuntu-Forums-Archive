---
title: "Restricted Drivers in Karmic RC"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Martin Marshalek on 2009-10-24
Sorry for putting this here but I can't find the Karmic forum. Anyway, I just installed the RC on my laptop (64bit) and the hardware drivers window tells me that "no proprietary drivers are in use on this system" and does not list any drivers in the window like previous releases did. Is there a new setting somewhere or how should I install nvidia and broadcom drivers?

---

### Post by philinux on 2009-10-24
> **Martin Marshalek said:**
> Sorry for putting this here but I can't find the Karmic forum. Anyway, I just installed the RC on my laptop (64bit) and the hardware drivers window tells me that "no proprietary drivers are in use on this system" and does not list any drivers in the window like previous releases did. Is there a new setting somewhere or how should I install nvidia and broadcom drivers?

[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

Whats your vid card model. It's still Hardware drivers. Have done an update yet, that might explain it.

---

### Post by Martin Marshalek on 2009-10-24
Thanks, from now on I'll go to that forum. Anyway, I have a broadcom wireless card and a Nvidia GeForce Go 6100 for video. I'll try an update and see what happens.

---

### Post by Bucky Ball on 2009-10-24
Yep, plug in an ethernet cable if you haven't already and perhaps reboot.

---

### Post by philinux on 2009-10-24
> **Martin Marshalek said:**
> Thanks, from now on I'll go to that forum. Anyway, I have a broadcom wireless card and a Nvidia GeForce Go 6100 for video. I'll try an update and see what happens.

If you dont get offered a driver just use synaptic and search for 6100 and choose the latest nvidia-glx-xxx.

---

### Post by Martin Marshalek on 2009-10-24
After the update I got drivers offered but they won't install. I'll try rebooting again.

---

### Post by philinux on 2009-10-24
> **Martin Marshalek said:**
> After the update I got drivers offered but they won't install. I'll try rebooting again.

It can take a while to install it has to download the driver first. Leave it to it.

---

### Post by Martin Marshalek on 2009-10-24
Well, I got impatient and killed the process before it finished but when I rebooted it said that the driver was activated and now everything works. I would assume that, if something was damaged or not installed right the package would be listed as broken right or should I just reinstall the wireless driver? For now the way I look at it is "Don't look a gift horse in the mouth" but...

BTW, thanks for all the help with Karmic Phil.

---

