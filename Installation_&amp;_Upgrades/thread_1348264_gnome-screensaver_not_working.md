---
title: "gnome-screensaver not working"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Castrato on 2009-12-07
I'm experiencing problems with Mythbuntu 9.10 gnome-screensaver.  It is not activating after the specified idle time.  When I first discovered this, I installed xscreensaver as an alternative solution.  This worked, but xscreensaver was activated while watching TV also not desirable.  Now I'm back to figuring out gnome-screensaver.  xscreensaver has been removed.

I have verified my screensaver settings in xfce by navigating to Applications | Settings | Screensaver.  I'm using a Blank Screen, regarding the PC as idle after 1min, and have opted to not lock the screen.

In the Power Management settings, the display is put to sleep after 5min on AC and 1min on UPS.

I have tried:
sudo dpkg-reconfigure gnome-screensaver
sudo dpkg-reconfigure gnome-power-manager

After verifying successful reconfiguration, I checked the settings in the GUI to insure they were still correct.  The screensaver would not work.

I have also tried:
sudo apt-get install gnome-screensaver --reinstall

This produces the same results.

I have not added any special screensaver hacks, xscreensaver has been purged, and I have never edited any of the conf files via shell.  I've also scoured the forums for users experiencing the same symptoms, but it seems like everyone is trying to figure out how to disable the screensaver rather than keep it on like I want to do.

Thanks for any input you can offer.

---

### Post by KiLaHuRtZ on 2009-12-07
This is a known bug, we are working on a patch.  Please assist in testing Marc Deslauriers' patch.  If there are enough reports confirming it resolves the issue, an update will most likely be added to the repositories.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/411350]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/411350")

---

### Post by Castrato on 2009-12-07
> **KiLaHuRtZ said:**
> This is a known bug, we are working on a patch.  Please assist in testing Marc Deslauriers' patch.  If there are enough reports confirming it resolves the issue, an update will most likely be added to the repositories.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/411350]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/411350")

According to his posts, mythbuntu is affected since it is based on xfce and does not use gnome-session.  Since gnome-screensaver relies on gnome-session to activate the screensaver, this is broken in *buntu using xfce.  Not sure what to do now.

---

