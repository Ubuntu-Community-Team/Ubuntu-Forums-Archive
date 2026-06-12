---
title: "initramfs hang"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by CaseyCaseyCasey on 2008-07-29
I recently installed xubuntu to a usb stick and after finding a computer that would boot from usb, stuck it in and tried booting.  It seemed to go quiet well for a while.  I can boot to the point where I get the 'XUBUNTU' logo with the blue bar, but after that loads i see white text on a black background which reads:

Busy Box v1.1.3 (Debian 1:1.1.3 - 5ubuntu12) Built-in Shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)


... however I can not enter 'help', neither does it proceed automatically to another stage, it just hangs there.

Anyone else encountered this?

---

### Post by spiderbatdad on 2008-07-29
There are a number of reasons this can occur. Possibly boot options are necessary. Possibly the alternate cd will provide a more compatible installation.

There is a screencast here:[http://screencasts.ubuntu.com/Installing_Xubuntu](http://screencasts.ubuntu.com/Installing_Xubuntu)

Boot options explained:[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you are dual booting, make sure windows has been shut down cleanly before booting into xubuntu.

---

