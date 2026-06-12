---
title: "Not detecting my SATA drive, can't install Ubuntu."
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by Posty on 2008-01-30
Well, here's the thing... I tried installing from both the normal Live CD and the Alternate CD, and both decide that they don't want to give me the option of installing to my SATA HDD. It detects my IDE drive as well as my external USB one, but not the one that I need to install Ubuntu on... When booting the Alternate CD's installation, I saw this error pop up and I think it might have something to do with the SATA drive.

ata2.00: failed to set xfermode (err_mask=0x40)

No idea if any of this is going to help... but the motherboard is an XFX nForce 680i LT SLI. Any ideas?

---

### Post by tenmoi on 2008-01-31
see this [http://ubuntuforums.org/showthread.php?t=393237](http://ubuntuforums.org/showthread.php?t=393237)

---

### Post by Posty on 2008-01-31
All I noticed on there was adding "irqpoll" to the boot params... However, that doesn't seem to work in my case. Any other ideas?

---

