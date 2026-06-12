---
title: "Pointless partitioning repetition/ GRUB failure"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Flandry on 2005-10-14
I'm not sure where to report this bug, so please point me to the proper location.

I got to the point where GRUB was to be installed.  Because i want access to the recovery partition on my Thinkpad T42, i declined installing it into the boot sector.  Then came the screen with other options.  Not remembering the exact partitioning of my drive, i assumed that the program would not be retarded enough to suggest the swap partition (the first partition of my extended partition) as a viable place.  So when i selected that option, the installer failed (This is a fatal error).  "No problem" i thought, i'll just go back and select the boot partition.  After checking the partitions again (by selected up "Partition Disks" option) to confirm that the boot partition was 6, not 5 (the swap partition suggested by install), i reselected "Install the GRUB boot loader on a hard disk".  Instead of presenting me with that page, the installer opened the "Partition Disks" page again.  Okay, i let it go ahead and repartition.  Now it gives an error "The grub package failed to install into /target/. ..." and refuses to either repeat the other steps (as would have made sense after forcing a repartition/reformat).  Anyway, the whole experience was a bit of unpolished UI aggravation at best.  I'll just reboot and start over... (elapsed install time: 1.2 hours)

---

