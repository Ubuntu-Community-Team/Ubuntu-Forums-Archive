---
title: "Display problems after turning screen off and back on"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by anjeon on 2011-11-09
Hello all,

I am upgrading one of my machines from 11.04 to 11.10, and ran into an issue I could use some help in resolving.  When I first boot the machine and log in, everything is fine.  My monitor (actually a Vizio HDTV connected via HDMI) is at it's native resolution of 1360x768.  If I turn the monitor off and back on again, it stays blank and says no signal.  If I switch to one of the full screen terminals (ctrl-alt-f2 for example) then it comes on.  If I then switch back to the desktop, it appears shrunken with black areas around it.  The monitor then reports it is at 1080p, not the native resolution I had it set to before.  I am also unable to change the resolution, it is stuck this way.

That is, stuck until I log out.  If I log out, then the log on screen resets the resolution back to native and everything is good again.

GPU is an integrated Radeon HD 3300 with Catalyst 11.10 driver.

Thank you for any assistance you can give.

---

### Post by MAFoElffen on 2011-11-09
> **anjeon said:**
> Hello all,

I am upgrading one of my machines from 11.04 to 11.10, and ran into an issue I could use some help in resolving.  When I first boot the machine and log in, everything is fine.  My monitor (actually a Vizio HDTV connected via HDMI) is at it's native resolution of 1360x768.  If I turn the monitor off and back on again, it stays blank and says no signal.  If I switch to one of the full screen terminals (ctrl-alt-f2 for example) then it comes on.  If I then switch back to the desktop, it appears shrunken with black areas around it.  The monitor then reports it is at 1080p, not the native resolution I had it set to before.  I am also unable to change the resolution, it is stuck this way.

That is, stuck until I log out.  If I log out, then the log on screen resets the resolution back to native and everything is good again.

GPU is an integrated Radeon HD 3300 with Catalyst 11.10 driver.

Thank you for any assistance you can give.
Sounds like what is happening is the same as what happens with TVs and HDMI on media servers... The problem is the card losses signal with the display , doesn't see a device, so losses sync with that devicet. (It forgets the data from the device) When you bumped it, it comes back up, but it doesn't know what mode it's in... Normally, you wouldn't turn a monitor off and back on...

Fix I kow for that is to edit your xorg.conf file to have a default resolution and a default dpi for that port/display.  Then you add a line to force output to that port so if stays on.  Optional is to create a locoal EDID file so that the EDID data is available even if the display is turned off.

If you want help with that, you would need to post your /etc/X11/xorg.conf and /var/log/Xorg.0.log files.

---

### Post by anjeon on 2011-11-09
Thanks for the help.  I added a default resolution to my xorg.conf file.  When I turn the monitor back on it still says no signal, but if I switch to a full-screen terminal and back to the desktop, it is at the correct resolution now.

I can live with the 2 extra keystrokes.

---

