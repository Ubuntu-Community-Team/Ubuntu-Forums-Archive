---
title: "Installing Ubuntu on eSATA HDD"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by phazonmutant on 2008-11-17
I apparently can't install Ubuntu on my FakeRAID main hard-drives due to a bug (they have a complex volume name, details [here](http://ubuntuforums.org/showthread.php?t=981568)), so I'm down to my backup plan.

Is it possible to install Ubuntu to an external hard-drive connected via eSATA?  Moreover, is it possible to install GRUB in such a manner that I can boot my windows machine (from the primary RAID volume) if the external hard drive is not plugged in?

---

### Post by caljohnsmith on 2008-11-17
> **phazonmutant said:**
> I apparently can't install Ubuntu on my FakeRAID main hard-drives due to a bug (they have a complex volume name, details [here](http://ubuntuforums.org/showthread.php?t=981568)), so I'm down to my backup plan.

Is it possible to install Ubuntu to an external hard-drive connected via eSATA?  Moreover, is it possible to install GRUB in such a manner that I can boot my windows machine (from the primary RAID volume) if the external hard drive is not plugged in?
Absolutely you can do that. :) Just make sure that in the final stage of the Ubuntu installer, you click on the "advanced" button and specify /dev/sdb (or whichever is your eSATA drive) to install Grub to; make sure you don't choose (hd0) or /dev/sda, as that is the internal drive. Then set your BIOS so that the external drive is first in the BIOS boot order; then when you disconnect the external drive, the internal drive should boot by default if it is next in the BIOS boot order. Let me know how it goes. :)

---

