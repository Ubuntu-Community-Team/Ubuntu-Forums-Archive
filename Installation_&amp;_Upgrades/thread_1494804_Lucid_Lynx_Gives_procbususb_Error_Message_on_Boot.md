---
title: "Lucid Lynx Gives /proc/bus/usb Error Message on Boot"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by charles s on 2010-05-27
I upgraded from Karmic Koala to Lucid Lynx using the Alternate Install CD (dialup is the only internet access I have, and I can't use the conventional upgrade mechanism that requires a 680MB+ download).  When I boot, I get a purple "ubuntu" screen with this error message in two lines:

"An error occurred while mounting  /proc/bus/usb"
"Press S to skip mounting or M for manual recovery".

When I press S, boot completes and I can use Lucid in an apparently normal way.  By the way, the USB ports on the back and front of my computer, as well as the built-in SD card reader, work perfectly.

My "/etc/fstab" file has in it the following line:

"proc            /proc           proc    defaults        0    0".

My "/proc" folder has lots of folders and individual documents in it, but I have no idea what, if anything, must be done in this folder, or what other changes I need to make to Lucid to get the right boot actions to happen so that this error message doesn't appear.  Can someone help me?

P.S. the "x_box" buttons for closing, minimizing, and maximizing windows are now on the left-hand side of the window's top line.  How can I move them back to the right side? 

Thanks

Charles S

---

### Post by charles s on 2010-05-27
SOLVED

This is my own "nut behind the wheel" error.  A year ago, I put a line in my /etc/fstab file that was intended to help me connect with my APC UPS battery backup.  This caused the error and, when I commented the line out, the boot process works as it should.  

Sorry for bothering those who read my original request.

Thanks

Charles S

---

### Post by charles s on 2010-05-27
By the way, I also solved the "Lucid Lynx buttons on the left-hand side of the window" problem.

Per a UK website, just go to "System", "Preferences", "Appearance", "Theme" and replace the default theme with another like "Human Clearlooks".  Like magic, the buttons will be back to where they should be.  Only the default themes have this bizarre change to the way Ubuntu has been configured since I started using Dapper Drake.

---

