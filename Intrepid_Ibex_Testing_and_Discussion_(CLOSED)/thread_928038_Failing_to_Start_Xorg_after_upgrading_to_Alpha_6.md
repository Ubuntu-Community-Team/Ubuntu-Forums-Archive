---
title: "Failing to Start Xorg after upgrading to Alpha 6"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by winrowc on 2008-09-23
I had alpha 5 and it was working great so I updated to alpha 6 last night. Compiz hadnt been working well recently so I tried installing the proprietary ATI drivers. I did the update and the installation of drivers all in one session, and when I restarted I got an error, and Xorg wouldnt load. I looked it up online and its [this bug]("https://bugs.launchpad.net/ubuntu/+bug/272639/+viewstatus"). Any suggestions to just get Xorg to load? I can deal without the proprietary drivers, as I understand they don't work well with Intrepid, but any of the GUI options (reconfigure, use backup etc.) all resulted in the same error. My xorg.conf as it stands is really basic with just "Configured monitor" and the like so it surprises me that its failing...

---

### Post by winrowc on 2008-09-23
I forgot to specify that ubuntu appears to load, but the screen turns black before the login screen, and if goes into the safe graphics mode.

Ugh this is frustrating; shouldnt the safe graphics mode work no matter what? I thought that was spose to function without the proprietary drivers...

---

### Post by Rashedul on 2008-09-23
I had a similar problem with a recent update.

Adding ```
Driver "radeon"
``` to my Display/Video section in xorg.conf helped. Other times starting recovery mode and running the x fix helps me.

---

### Post by RAOF on 2008-09-23
This is likely a problem with the fglrx drivers failing to support our X server.  Actually, there's worse -  while having the fglrx drivers *installed* has always broken 3D for any other drivers, it seems the current fglrx drivers also include their own, old, copy of libdri, which means that X will not start *at all* with the fglrx drivers installed.

Removing the **xorg-driver-fglrx** package should at least allow X to start for you; depending on what card you have, this should also give you 3d acceleration.

---

