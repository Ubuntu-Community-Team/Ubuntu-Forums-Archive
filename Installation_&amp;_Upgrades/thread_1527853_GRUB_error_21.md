---
title: "GRUB error 21"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by Chris1274 on 2010-07-09
I installed Ubuntu 9.04 on a second HD (Dell Dimension 2400, with winXP on the main HD), but once the installation was complete and the computer was restarted, the boot process stalled out almost immediately, showing "error 21" in GRUB. From what I understand, that means GRUB can't find the second HD.

In an effort to fix it (following some suggestions I read elsewhere), I went into the startup menu and changed "slave hard drive" from "off" to "auto". That made things worse, as I started getting keyboard errors and it looked like I really f---ed things up. Thankfully I was able to get things back to where they were, but that still leaves the original problem. 

S.O.S.

---

### Post by Chris1274 on 2010-07-10
Well, I managed at least to get winXP back by booting from the CD and fixing the master boot record. Only now it's as if the second HD has disappeared altogether.

Help would be much appreciated here.

---

### Post by Chris1274 on 2010-07-10
So I went into the disk manager and the drive appears to be enabled. I guess windows just doesn't recognize it as a storage device because of the way it's now formatted.

I'm going to try to replace Jaunty with Lucid on it. I understand that Ubuntu switched from one version of GRUB to another with Karmic, which may have worked out the error 21 bug. Wish me luck.

---

