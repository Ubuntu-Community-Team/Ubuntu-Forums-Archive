---
title: "Fresh install Ubuntu 14.04.03 boots every second time"
date: 2016-01-19
forum: Installation &amp; Upgrades
---

### Post by khurtsiya on 2016-01-19
Fresh install. One boot is blank purple screen, second boot - normal (prompt for encryptoin pw), third - blank purple, forth - normal and so on. Can this be fixed?

I use entire disk encrytption LVM

---

### Post by kansasnoob on 2016-01-20
I'm not at all sure but could this possibly be a graphics driver issue? While booted into the desktop you might look to see if an Additional Driver is available:

[http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers](http://askubuntu.com/questions/47506/how-do-i-install-additional-drivers)

---

### Post by khurtsiya on 2016-01-20
Well this is not explain why one boot is fine and boot after it fails... I found that this only happens when I install with full disk encryption.

Anyway I ended installing 14.04.1 which has no such problem and then upgraded it.

---

### Post by kansasnoob on 2016-01-20
Ah, 14.04.3 shipped with the Vivid kernel and X-stack rather than the OEM Trusty HWE:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

So it was clearly either a kernel problem or X related.

---

### Post by yancek on 2016-01-20
I had a similar problem when I first install 14.04.1 shortly after the initial release.  The difference was that I got horizontal dashed lines across the top half of the screen and the bottom half of the screen was black.  If I immediately re-booted it would boot with no problem to the login screen and everything worked.  This wasn't my primary system so I kep track over a period of several weeks and the same thing happened whenever I booted, second time always booted, the first never did.  I installed the Nvidia drivers and that didn't change anything.  I eventually just re-installed it from the same flash drive and it's been working fine since.  Haven't got a clue as to why that happened.

---

