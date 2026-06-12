---
title: "[SOLVED] Digital Camera no longer mounts in gutsy"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by brydong on 2007-11-05
Since upgrading to gutsy my Nikon digital camera no longer mounts when plugged into usb port. I tried the fix described here...[http://ubuntuforums.org/showthread.php?t=330384](http://ubuntuforums.org/showthread.php?t=330384)

using the output from lsusb:
Bus 005 Device 025: ID 04b0:040f Nikon Corp. 

and restarting udev.

That does NOT appear to have fixed the issue.

Help?

---

### Post by brydong on 2007-11-06
This issue is FIXED by changing the camera from mass-storage to PTP mode.

---

### Post by mutzinet on 2007-12-02
Thank you for the fix, got the same problem here...

---

