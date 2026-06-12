---
title: "Garbled screen"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Rancoras on 2007-04-23
Hello, it's been awhile since I lurked these halls.

Feisty lured me back for another look at Ubuntu.  I downloaded the liveCD / install disk for X386.  The liveCD seems to boot fine until what I can only assume is the login screen loads.  (This is before I have tried to install anything)  I have to assume because the screen is garbled and I can't see anything.  Ctrl + Alt + Backspace reloads the screen to the same behavior.

I'm very rusty with Ubuntu, so can anyone give me a hand as to what to try?

My specs:
Athlon X2 4600+
Asus M2N32-SLi motherboard
Seagate Barracuda 250GB SATA HDD (7200 RPM)
2GB Crucial memory
Plextor PX755SA SATA DVD burner
Creative X-Fi MusicExtreme soundcard

If you need any other info, let me know.

---

### Post by bwhite82 on 2007-04-23
You didn't list what video hardware you have, but more than likely, installing the correct driver for it will fix your problem. Check out [http://wiki.ubuntu.com](http://wiki.ubuntu.com) which is a great source of information.

---

### Post by Rancoras on 2007-04-23
Damn, I knew I forgot something.

Nvidia 7600GT

This all is just when starting the liveCD.  I haven't been able to install anything yet.

---

### Post by Rancoras on 2007-04-25
I fixed it.  After playing with the init string options when pressing F6 on the liveCD boot menu, I found that removing "xforcevesa" allowed the desktop to load.

---

