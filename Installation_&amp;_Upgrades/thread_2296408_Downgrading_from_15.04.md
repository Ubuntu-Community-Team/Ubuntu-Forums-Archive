---
title: "Downgrading from 15.04"
date: 2015-09-25
forum: Installation &amp; Upgrades
---

### Post by Zachary_Cormier on 2015-09-25
Hey, I'm dual booted right now with 15.04 and windows 10. I want to downgrade to 14.04. I was wondering what steps I go through. Do I just use the install along side windows the same as a fresh dual boot, or do I have to do something else to get the partitioned drive space back?

---

### Post by Dennis N on 2015-09-25
From the 14.04 installer, I would use the "something else" option on the "preparing to install" page, then on the next screen, select the existing 15.04 partition, click "change", then in the dialog, specify ext4 journaled filesystem, mount point as /. Check the "format" box for the partition. Pay attention to the bootloader location at the bottom - should be installed to the same drive, such as sda. Then you can click "install now".

---

