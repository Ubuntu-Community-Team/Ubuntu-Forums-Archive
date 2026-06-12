---
title: "Ubuntu 8.10 alpha4 is freezing"
date: 2008-08-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tr333 on 2008-08-24
Ubuntu 8.10 alpha4 is sometimes freezing.  I'm not sure when or where it happens since I sometimes turn the computer on a few minutes before I switch on the TV (Mythbuntu connected to TV-OUT/SVIDEO).  The only major change I have noticed over 8.04, where everything was fine, is the wireless driver changing from madwifi to ath5k.  How can I determine what is causing the system to hang?

---

### Post by Nullack on 2008-08-24
blacklist the driver and do some tests :)

---

### Post by jaymode on 2008-08-24
Mine is also freezing. I suspect the nvidia driver. I haven't had a chance to fool around with it yet though.

---

### Post by tr333 on 2008-08-25
I have just confirmed the ath5k driver to be the culprit.  I unloaded the driver from VC #1 and then reloaded it, and everything just froze.  I am also using the latest nVidia driver available in repos and haven't experienced any problems with it yet.

---

### Post by jaymode on 2008-08-25
Are you using C1E for power savings on your CPU. Seems like it could be a potential problem, I am going to disable it tonight and see how that works for me.

[http://ubuntuforums.org/showthread.php?t=900286](http://ubuntuforums.org/showthread.php?t=900286)

---

