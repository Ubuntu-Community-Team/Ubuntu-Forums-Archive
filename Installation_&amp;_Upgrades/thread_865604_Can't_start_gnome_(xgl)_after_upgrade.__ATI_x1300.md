---
title: "Can't start gnome (xgl) after upgrade.  ATI x1300"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by FishFoot on 2008-07-20
Hey everybody,

I was happily running Feisty with 2 monitors on an ATI Radeon X1300 and decided to upgrade for better ATI support.  I did an upgrade to Gutsy and afterward couldn't start the GUI at all.  After trying a couple of different package upgrades I decided to just try to upgrade again to Hardy.  Everything worked and GDM starts up.  Unfortunately I can't get any actual sessions to start.  I get a message that says "Your login lasted less than 10 seconds..." and then I get kicked back to the main GDM menu.  When I try to start a failsafe session I get a white box in the top right corner (which looks like an error message) but no text appears.  At that point it just hangs.

I am told to look at the ~/.xsession-errors file which has the following:

> 
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama 
xmodmap:  unable to open display ':2'

(x-session-manager:12193): Gtk-WARNING **: cannot open display: :2


---

### Post by Pumalite on 2008-07-20
Try with one Monitor first. Later configure the other.

---

### Post by FishFoot on 2008-07-21
Hey, thank you for the response.

I tried that... sort of.

I went into my /etc/X11/xorg.conf and removed references to the second screen and the second device.  I then restarted X.  The system came back up using both monitors but this time xinerama was stretching the login across both screens.  The login box itself was in the middle of both monitors.  I believe I saw the same error message but I'll have to double check that when I get home tonight.

I then went into the xorg.conf and set xinerama = off and restarted X.  Again, I think I got the same error message but I'll have to check tonight.

Can anybody tell me if I've shut the second monitor off correctly?  Is there any way to fully disable xinerama?

Thanks
FishFoot

---

