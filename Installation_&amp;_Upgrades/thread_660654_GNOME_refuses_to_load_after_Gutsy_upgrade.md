---
title: "GNOME refuses to load after Gutsy upgrade"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by jolt256 on 2008-01-07
After fixing a problem in which the newly-upgraded system didn't detect one of my RAID arrays (causing LVM to panic, and nothing to get mounted), I'm having trouble getting a graphical desktop on my machine. After the Feisty->Gutsy upgrade, trying a standard login would hang for a couple seconds, and then trigger a reload of the X server. Failsafe GNOME worked, though.

I assumed the problem had to do with my leftover installation of beryl, from pre-upgrade, so I nuked the entry for beryl-manager in System-Preferences-Session-Startup Programs. Now even the failsafe GNOME session hangs on loading. Specifically, it plays the startup sound, and then hangs at the brown desktop background. Neither the desktop icons nor the panels load, although the mouse pointer is visible, and the fade-to-black screensaver kicks in after its normal delay.

'Failsafe terminal' works; from there I can load metacity and run gnome-session, which does the same thing as logging in with failsafe GNOME - I hear the startup sound, but nothing else happens. Trying to run gnome-session-preferences fails with an error that it can't connect to the session manager.

I've tried reinstalling all the gnome packages:
```
sudo apt-get install --reinstall `dpkg -l 'gnome*' | grep ii | tr -s ' ' | cut -f2 -d\ `
```

But that didn't help either. Does anyone have ideas on how to solve this problem, or at least to get a trace of what's failing where? I'm running the latest drivers from Nvidia's site (169.07), and Xorg.0.log confirms that they're loading fine (including the GLX extension).

---

