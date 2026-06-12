---
title: "Upgrade problem:  packages not installable"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by snakyjake on 2008-10-22
I'm in the process of upgrading from 7.0 to 8.0 via Adept.

However, during the process I received some errors.  I tried fixing the errors and now I'm lost.

Now when I retry the upgrade and run:  **aptitude safe-upgrade** from a console, I receive:

> The following package have unmet dependencies:
xserver-xorg: Depends: xserver-xorg-core (>=2:1.4-3) but is not installable

Depends: xserver-xorg-video-all but it is not installable or exserver-xorg-video-2 which is a virtual package.

xserver-xorg-input-wacom: Depends: xserver-xorg-core (>= 2:1.3.0.0) but it is not installable.

kexi: Depends: libpqxx-2.6.9 but it is not installable.

When I tried fixing the errors, I tried:
aptitude update
aptitude full-upgrade
dkpg --configure -a

I didn't do anything else or edit anything.

I have now rebooted the machine, and the bootup takes me to the console, not KDE or Gnome.  Cannot use startx or startkde.

Please help!

---

