---
title: "strange XServer behaviour"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by globetrotters1 on 2006-07-23
With the kind help of an Austrian Linux guru I could make a 3-screen setup work just fine - except when the system starts or reboots

The first time the XServer starts the resolution on the screens 2 and 3 are something like 1280x1024 instead of 1600x1200... only screen 1 is correct!

But the xorg.conf file must be correct - because when I restart the XServer with ctl-alt-back all 3 LCDs switch to 1600x1200!

Who experienced that same behaviour too and how can I resolve it?

Any help would be very much appreciated, thanks

Martin
globetrotters1

PS: setup is a dual AMD64 Opteron board with Matrox G450 MMS graphics adapter - running on Dapper 32-bit (because the Matrox driver is not available in 64 bit) upgraded from Breezy 5.10

---------------------

after installing Dapper from scratch:

same strange behaviour! might be a bug in the Xorg software (Xinerama)...

---

