---
title: "No Client Screen Update When Running VNC over Vino"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by paragonconcept on 2009-12-27
i just updated from ubuntu 8.10 to 9.04 - and now when i vnc into my ubuntu box over vino-server via JollyFast VNC & Chicken VNC on OS X - i get control over the desktop - but the feed on my laptop only shows the screen state of when i logged in - its like a static image of the desktop.

I have my media center hooked up to a TV, and i can see the desktop is running fine, so its just a VNC issue.

---

### Post by bradcrittenden on 2009-12-28
I experienced the same problem today trying to connect to a 9.10 desktop.  This bug ([https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/353126)) mentioned turning off compiz (System - Preferences - Appearance - Visual Effects to None) should allow remote connections to work, and it did.

Good luck.

--bac

---

