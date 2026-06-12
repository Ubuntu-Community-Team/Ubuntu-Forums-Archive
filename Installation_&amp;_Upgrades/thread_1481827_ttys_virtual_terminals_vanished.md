---
title: "ttys virtual terminals vanished"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by sinistertim101 on 2010-05-13
I am using 9.10 and my ability to "ctrl + alt F-dey" to a ttys shell no longer is available after running an update. 10.04 has the same bug. Getty is installed and I can not figure out what happened.

How do I get ttys back?

---

### Post by efflandt on 2010-05-13
Did you by any chance enable kernel mode (KMS) video drivers in 9.10?  When I did that in Karmic I lost the console terminals.  They worked in Lucid, but that uses KMS by default and I had other issues with that, so I disabled it with nomodeset kernel parameter.

What is the output of **dmesg | grep drm**

---

### Post by sinistertim101 on 2010-05-13
tim@Sashimee:/usr/src/linux-headers-2.6.31-21$ dmesg | grep drm
[    2.272458] [drm] Initialized drm 1.1.0 20060810
[    2.291235] [drm] radeon default to kernel modesetting DISABLED.
[    2.291987] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[   15.888142] [drm] Setting GART location based on new memory map
[   15.889338] [drm] Loading RS690/RS740 Microcode
[   15.889360] [drm] Num pipes: 1
[   15.889368] [drm] writeback test succeeded in 1 usecs
[   26.308122] [drm] Num pipes: 1
[   33.742433] [drm] Loading RS690/RS740 Microcode
[   33.742453] [drm] Num pipes: 1
tim@Sashimee:/usr/src/linux-headers-2.6.31-21$ 

I am installing the linux kernel to enable modesetting manually.

---

### Post by wojox on 2010-05-13
Did you edit that file /etc/init.d/rc and change CONCURRENCY=none to CONCURRENCY=shell?

I did that once and lost my ability to Ctrl+Alt+F1-F6

---

