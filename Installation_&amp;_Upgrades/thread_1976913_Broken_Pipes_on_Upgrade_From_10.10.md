---
title: "Broken Pipes on Upgrade From 10.10"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by demonboy on 2012-05-09
I've had to put my wife on my old netbook which had 10.10. Wanting to upgrade to 11.10 I set her off only for the upgrade to get half way through, reboot, and now come up with the 'broken pipes' message. I cannot run any of the earlier installed versions and tried running in safe mode to repair packages, which told me I had 20mb worth of packages to finish installing. But what now? Any pointers?

---

### Post by Peter09 on 2012-05-09
In safe mode do:
 
```
sudo apt-get upgrade
```
 
see what happens.
 
Sorry that should be recovery mode.

---

### Post by demonboy on 2012-05-09
OK, but how do I go online? I'm on a 3G dongle with no chance of hard-wiring.

---

### Post by Peter09 on 2012-05-09
Ouch, that may be a problem, it depends where your system crashed. The upgrade normally downloads all the files first and then installs them. You may have a lot of the files already on your machine. If so it will install them, worth a try.
 
If this fails, try putting the live CD in the drive. I have seen update manager offer to install from that source when available, thats a long shot.

---

### Post by demonboy on 2012-05-09
Thank you, Peter. Will do this first thing tomorrow (it's getting on here in India). Thank you for your time.

---

