---
title: "Blank black screen on Latitude D610"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Kensey on 2007-10-20
I just upgraded my Dell Latitude D610 (945GM integrated Intel graphics) to Gutsy using update-manager.  The upgrade seemed to go OK, the system restarted and I was able for the first time ever to select native resolution (1400x1050) for my desktop without using 915resolution.  Then the update-manager told me that updates were available for compiz and compiz-plugins.  I let it go ahead and do the updates.

At the same time I was looking at the selected video driver.  It was i810.  I selected by manufacturer and model and it continued to use i810 -- OK, whatever.

Suddenly the screen went black and there was some drive activity, then nothing.  No text console with Ctrl-Alt-F1, no desktop.  Rebooted to the same thing.  Tried rebooting to recovery mode -- same thing.  I even tried booting an older kernel and actually got a text scroll as boot processes ran, but still ended up with a black screen.

What do I do now?

---

### Post by skzo on 2007-10-20
hey, for some reason, the driver i810 stoped working in gutsy... just reboot in recovery mode, give password for maintance, login and edit /etc/X11/xorg.conf and edit the driver, change from i810 to intel and it should work.

although this driver gives you 3d accel it's not as fast as the i810.... and i can't get anymore awnsers... sorry

---

### Post by Kensey on 2007-10-20
> **skzo said:**
> hey, for some reason, the driver i810 stoped working in gutsy... just reboot in recovery mode, give password for maintance, login and edit /etc/X11/xorg.conf and edit the driver, change from i810 to intel and it should work.

Actually the i810 works fine for me.  I ended up figuring out the problem right after I posted -- I booted the older kernel in recovery mode, added 915resolution to /etc/rc.local, rebooted and was able to log in.  Then I had really slow desktop redraws so I uninstalled Xgl and restarted the session.  Since then everything's been great, although I still don't have usplash...

---

