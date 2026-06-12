---
title: "Upgrading Ubuntu 10.10 to Natty - will it format my entire PC?"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by MrRichard on 2011-01-08
The last time I attempted to install an alpha release, my entire hard drive was wiped out (thankfully it was backed up) because of my ignorance to the installation warnings :).

Would it be possible upgrade Maverick Meerkat to Natty without editing any partitions?

---

### Post by oldos2er on 2011-01-08
Why not wait until Natty is officially released?

---

### Post by efflandt on 2011-01-08
There is a different forum for Natty while it is still under development [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Long before alpha1 I tried to upgrade a Maverick system to Natty per instructions in that forum, and it did not work due to dependencies.  So instead I was running it from 8 GB USB stick, and since alpha1 have been running it from internal SSD.  Natty has had some teething problems until recently due to library and python version changes and sorting out compiz and unity, but it is running smoother for me the past few days.

If you are bold you could try upgrading and see if it works now.  If you do a fresh install, you should pay attention to what you are doing with manual partitioning (I never trust automatic partitioning).  And if you install it on external hd or flash, pay attention to bottom of manual partition screen to select where to install grub.

When you login **Ubuntu Desktop** is the new desktop with Unity, but that only works if you have 3D (glx) support.  **Ubuntu Classic Desktop** is like Maverick.  And there is also **Ubuntu Desktop (Failsafe)**.  But not sure how the latter 2 work now, because earlier I had trouble with applets and panels crashing in those (sometimes ending up with nothing but background image).  So you might not want to go with Natty for your main or only system just yet.

---

