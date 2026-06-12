---
title: "Compiz crashes all the time w/ non-fglrx drivers"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by vaiocomputer on 2010-05-05
Compiz is utterly unusable, ever since probably about 9.04 or 9.10, when Ubuntu took out the Catalyst drivers for my laptop w/ Mobility Radeon HD 2300 their less capable open-source variants, which crashes after about 15 minutes of use.  

The screen gradually becomes less responsive for about 5 seconds, until it just completely freezes and becomes completely unresponsive to any keyboard or mouse commands.  I tried using the RadeonHD drivers instead and the problem is still there.  The 'Hardware Drivers' app in System > Administration doesn't seem to do detect any fglrx drivers for my system.

How would I get some working fglrx drivers back?

And I don't want to use Metacity anymore.

---

### Post by Peter09 on 2010-05-05
Have you got any drivers in System->Administration->Hardware
 
I had two drivers, one was enabled, by disabling that one and enabling the other I got a workable graphis capability - still not good but it does work.

---

### Post by vaiocomputer on 2010-05-05
No.  There are no drivers listed in Hardware Drivers

---

### Post by Peter09 on 2010-05-05
Check that you do not have an /etc/X11/xorg.conf, if you do rename it and reboot.

---

### Post by vaiocomputer on 2010-05-05
I don't have a 'xorg.conf', but 9 different ones, 3 are 'backup's, one is a 'failsafe', 3 w/ 'upgrades', and two are without just plain 'xorg.conf' with a ."2009053125"... at the end.

So, I'll just leave the failsafe one there and try your advice.

---

### Post by vaiocomputer on 2010-05-05
Nope, still no drivers in Hardware Drivers.

---

### Post by alphacrucis2 on 2010-05-05
> **vaiocomputer said:**
> Nope, still no drivers in Hardware Drivers.

There never will be. ATI dropped support for you card. You would have to use Catalyst 9.3 or earlier, which means going back to an old version of Ubuntu that has kernel and xorg compatible with Catalyst 9.3. If it isn't working with the OSS driver then report bug in launchpad.

Correction. I just had a look at the AMD site and HD 2000 series is still supported by Catalyst 10.4. Assuming your card really is a 2000 series card it should still be supported by the current fglrx. You could try downloading the Catalyst 10.4 Linux binary installer from the AMD site and **carefully** follow the instructions on their web site to install it.

---

### Post by McMichael96 on 2010-05-05
I would recommended getting a new GPU card. Maybe a nVida one as nVida works best on Ubuntu.

---

### Post by alphacrucis2 on 2010-05-05
> **McMichael96 said:**
> I would recommended getting a new GPU card. Maybe a nVida one as nVida works best on Ubuntu.

I believe the OP has a laptop so he can't really change his GPU

---

