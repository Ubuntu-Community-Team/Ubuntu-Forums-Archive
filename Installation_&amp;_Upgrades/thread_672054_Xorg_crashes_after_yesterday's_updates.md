---
title: "Xorg crashes after yesterday's updates"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by arsenix on 2008-01-19
Since yesterday's update my xorg will no longer stay up.  It appears to happen when I leave my machine alone for a while (maybe xscreensave or power management?).
End of Xorg.log.old after X restarts itself:
> 
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
SetGrabKeysState - disabled

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c95d1]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting


Never seen the "SetGrabKeysState - disabled" in my log before so this might be related.  Any ideas?  Anyone else having this problem?

James

---

### Post by samkline on 2008-01-19
I can't log in to GNOME anymore. It changed the screen resolution so I changed it back then logged off, then I tried to log in and it flickered black, then about 2 seconds later I was back at the GNOME login screen.

I'm using KDE now. Eww ;)

---

### Post by arsenix on 2008-01-19
Since I posted I fixed the issue.  Turns out it was xscreensaver crashing the machine... and it turns out all 3d apps were crashing it.  Reinstalled NVIDIA driver and now back to normal.

James

---

### Post by vratnica on 2008-01-19
always when I want to check for updates I have a fear that something will go wrong

this time, after updating the xorg, xorg takes over 80 % of my cpu everytime I scroll

is there some posibility to downgrade an update? to go back to last setting?

---

