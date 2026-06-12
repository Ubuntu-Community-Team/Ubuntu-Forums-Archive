---
title: "So who needs desktop icons anyway? BUGFIX for: STARTING FILE MANAGER ad infinitam...."
date: 2015-05-20
forum: MINT
---

### Post by lafeyette-management-y on 2015-05-20
So, today, I ran into yet another problem with Mint 17.1--but thought I'd post here, since it might apply to users of the underlying Ubuntu 14.04.

The problem is that "Starting file manager" repeats over and over again as the system starts up.  Under Mate ('buntu MATE), this might manifest as "Starting File Manager" buttons appearing and filling up your menu bar.  On other distros, it might just be that your system becomes very slow and unresponsive or that applications may not start despite clicking (hammering) on their start buttons/icons....  Or even a combination of these.

In any event, I ran into it with Mint 17.1 Mate Edition, and the solution seems to be to edit 
/usr/share/applications/caja.desktop and find the line (buried deep, but it's there!)  that says X-MATE-AutoRestart=true and change that to X-MATE-AutoRestart=false.

In the case of nautilus, the instructions would be to edit a similar file, /usr/share/applications/nautilus.desktop, and set AutoRestart to false.  

NOTE:  It may be "autorestart" instead of "AutoRestart".

Note also:  This work-around DOES disable desktop icons!  (No great loss in my book--they just make a clutter of things.)

---

### Post by howefield on 2015-05-20
Thread moved to the "*MINT*" forum.

---

