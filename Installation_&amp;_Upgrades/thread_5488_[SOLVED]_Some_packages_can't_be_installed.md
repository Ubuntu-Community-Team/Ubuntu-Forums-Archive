---
title: "[SOLVED] Some packages can't be installed"
date: 2004-11-19
forum: Installation &amp; Upgrades
---

### Post by shinkaide on 2004-11-19
I've downloaded the warty release 4.10 for i386 pcs and installed it. It went well, but the X server won't load! 

I tried installing everything again, and this time I checked some of the installed packages / not installed packages. There were some packages for Xfree86 that weren't installed, and I don't know why. If they weren't on the CD, they'd be categorized under "virtual packages", right?

---

### Post by randy on 2004-11-19
What's the X error output?  You might not have to worry about some packages not being installed.  If they aren't installed they probably aren't needed.

---

### Post by shinkaide on 2004-11-20
I've finally installed it, but I had to tinker around apt. I had to manually select the remaining packages under notinstalled-x11-main- ...  only then did x launch properly. Not to mention the packages for firefox and whatnot.

I did get some error messages like "Ack! Something bad happened while trying to install the packages" or something, when it came to installing the totem media player.

One thing that really bugs me the most is that pretty much everything installed okay except for any sort of ppp program. I can't connect to the internet! I have pppconfig and can run it, but I don't have a dialer...

---

