---
title: "Jaunty 9.04 - No trackpad on Lenovo N200"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by birdd on 2009-03-26
I've decided to try Jaunty 9.04 on my Lenovo N200, everything seems to be working except the trackpad. Any ideas? a USB external mouse works fine...

---

### Post by wjp.reg on 2009-03-26
Can you check to see if the Synaptics Touchpad driver is installed?

Should be xserver-xorg-input-synaptics, version 0.99.3-2ubuntu3, available and installed.

cheers

---

### Post by birdd on 2009-03-26
No it wasn't installed... I've installed that and rebooted and now its working... strange that it didn't detect it in the install. The live CD didn't detect it either, neither did the install... Yet when i did install 8.10 it was fine...

---

### Post by taavikko on 2009-03-26
> **birdd said:**
> No it wasn't installed... I've installed that and rebooted and now its working... strange that it didn't detect it in the install. The live CD didn't detect it either, neither did the install... Yet when i did install 8.10 it was fine...

This issue were documented in "Known issues"
[https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview](https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview)

But apparently it's been fixed in alpha6, it was still an issue in alpha5

Anyway, it's always good to check that page when upgrading or installing
Just fix the URL upon new release ;)

---

