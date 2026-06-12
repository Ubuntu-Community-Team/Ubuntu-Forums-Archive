---
title: "[SOLVED] Updates...system now dead"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by WhatIsChazaq on 2008-08-24
I ran updates earlier.

Stalled at a line stating "Installing Locales..."  I let it stay overnight.  Powered off, back on.  I can log in, but it just goes to a blank screen with a cursor (the cursor does move around).

Fix it?

Or how do I boot off the liveCD and access the folders on the drive to safe the data so I can re-install clean?  I boot off the LiveCD...but the folders say I don't have permission - how do I gain permission (I know the username and password).

Thanks!

---

### Post by meanburrito920 on 2008-08-24
boot into recovery mode from GRUB and select the 'fix packages' option

 If you just want to save the data, go into a terminal on the live cd and 'sudo su' into root. Then run 'nautilus' from the command line. the browser window that opens will give you privileges to everything.

---

### Post by WhatIsChazaq on 2008-08-24
Already tried to fix packages...no Good!

Nautilus is running...looks like I have full access to the folders...but I'm now getting "failed to mount" when I plug in an external 500gb usb drive.

Ideas?

Thanks a ton!

---

### Post by WhatIsChazaq on 2008-08-24
Never mind...it had not been cleanly shut down (usb drive).

Got it fixed.

---

