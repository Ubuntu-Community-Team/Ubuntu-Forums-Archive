---
title: "Ubuntu Installation Questions"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by kife@mail.utexas.edu on 2007-06-06
I am trying to install Ubuntu, but the problem is i have 2 identical hard drives with one of them having Windows XP on it. In the install menu, both of them are "SCSI" hard drives with one being 3 and the other being 4. Which one is the one with my Windows? Also, since I am going to be dual booting, do I install grub before or after Ubuntu?

---

### Post by arkham on 2007-06-07
Grub will be installed as part of your standard Ubuntu install at the end and should pick up the windows partition and allow you to boot for it.

As for which drive has windows on it already, when it comes to the partitioning part of the install, the drives will be displayed with more information - like partitions, filesystem type etc.  It  should be easy to figure out which one is which at that point.

If you are till in doubt, boot into the live CD and browse the drives to see which one has your windows files on it.  They should both get mounted under /media/sdXX where XX is a1, b1 etc.

The SCSI part of the description just means that they are probably SATA drives rather than IDE - both SCSI and SATA are serial interfaces rather than parallel like IDE and so use similar drivers, and linux treats them the same way - but SCSI was around first so you still see that description here and there.

---

