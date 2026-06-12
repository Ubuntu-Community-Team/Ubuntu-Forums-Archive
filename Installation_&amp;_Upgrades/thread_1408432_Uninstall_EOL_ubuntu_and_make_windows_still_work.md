---
title: "Uninstall EOL ubuntu and make windows still work"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by Red Nick18 on 2010-02-16
I haven't used Ubuntu in a little while and have an older version of Ubuntu.  I would like to completely remove Ubuntu and start over.  I currently have Ubuntu and Windows Xp home edition installed and am using the Grub loader for my MBR.  I used partition magic to change my partition from NTFS to Fat32 for the ubuntu part and then just NTFS for windows.  Id like to put the partions all back to the same and then resize the one partion to two NTFS's  Is this possible and if so Id like to know how preferable without partion magic and getting the newest version of Grub loader.
Thanks
Red Nick18

---

### Post by darkod on 2010-02-16
If you plan to install ubuntu again why making the partitions ntfs? And why one big one (if I understood correctly) which you would have to shrink later to make space for ubuntu?

Or you are talking about wubi install which is done inside windows? Not on a dedicated partition?

---

### Post by howefield on 2010-02-16
If you are talking about a "real" dual boot, with Ubuntu and Windows on separate partitions, boot up with the live Ubuntu CD to the desktop, and using GParted from the System > Administration menu, delete the partitions you don't want, and create what you do.

I'd suggest creating / /home and swap.

Then hit the Install icon on the desktop, and when you get to the partitioning part, mount your pre created partitions accordingly and install.

The number of issues on these boards with the Grub2 means I'd be reluctant to recommend it, but ymmv. :)

There are a few short videos explaining partitioning/installing/dual booting at screencasts.ubuntu.com

You may profit from watching them.

---

