---
title: "ubuntu not booting up"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by mypanda on 2010-06-24
Hi, I'm running ubuntu for the first time. I have it install in Windows xp and boot it up after restarting the com. But I'm unable to boot up ubuntu.  I can however go into the recovery failsafe mode.

How should I debug the errors? Thanks

---

### Post by oldfred on 2010-06-24
Welcome to the forum.

If you can get to the recover screen, you should run updates and see if you can start the graphics system. Many are having issues with video cards and find adding nomodeset in place of quiet splash on the boot line gets into the graphics with low resolution and then installing a hardware driver for the card works. 

At the grub menu type e for edit and scroll to the kernel line and replace quiet splash with nomodeset. control x to continue boot.

---

