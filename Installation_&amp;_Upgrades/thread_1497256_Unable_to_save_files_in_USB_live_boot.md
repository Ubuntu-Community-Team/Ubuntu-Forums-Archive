---
title: "Unable to save files in USB live boot"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by eaglelord on 2010-05-30
Hi.,

I am using Ubuntu USB live boot for my office, i created one using STARTUP DISC CREATER in UBUNTU 10.04. But i am unable to save files in the flash drive during the session in live boot. 
Because in Start up disc creator of Ubuntu 10.04 options like "stored in reserved space" is disabled, unlike ubuntu 9.10

kindly help me to save files during the session in USB boot...

---

### Post by ajgreeny on 2010-05-30
You need to set up the persistent install so you can use the usb disk for storage when you burn the image to the usb.  I am not sure if you can do it later, but have a look with a live CD if you can and see if you can shrink the partition on the usb with the live install on it and make a new partition in the freed space, now available.

---

### Post by garvinrick4 on 2010-05-30
Redo the Live USB and slide the bar on bottom of page to use 4gig of persistence. Without
persistence Live USB will just not hold any changes.

---

