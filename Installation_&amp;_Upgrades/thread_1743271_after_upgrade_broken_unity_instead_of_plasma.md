---
title: "after upgrade broken unity instead of plasma"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by m0llusk on 2011-04-29
Upgrade of kubuntu to 11.04 from 10.10 using kpackagekit appeared okay, as did the reboot and login from the new panel.  Then, instead of seeing my custom background and plasma desktop all I see is the color wash of the Unity background.  There is a right button menu in this desktop with a Create Launcher option that allows me to make launchers for konsole, firefox, and ksystemlog.  Windows come up, but with Unity window decorations.  Sure enough unity-window-decorator is running, but there is no plasma.  System logs don't reveal anything obvious that failed.  There is a kdm process running and kdeinit4 appears to have tried to start klauncher and kde4, but they are not actually running.

It seems like somehow GNOME and Unity have somehow collided with the KDE environment.  Possibly this might be fixed by reinstalling the kubuntu-desktop package?  That seems kind of heavy since everything is working which suggests this is a configuration issue possibly with something failing over somewhere along the line.

---

### Post by m0llusk on 2011-04-30
Problem Solved:  It turns out that the login panel (kdm) attempts to start GNOME Unity after the upgrade, but clicking the selector on the bottom of the login panel enables KDE Plasma to be selected.  I did so and now everything is beautiful again.  Yay!  I love Plasma so much!  Many thanks to the helpful persons on the #kubuntu IRC chat channel!

---

