---
title: "Help reinstall windows xp!!!!"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by frank2bones on 2011-01-09
I Have Installed Ubuntu on my system but am Wanting to Reinstall Windows XP but I keep getting a crash screen when it reads (Loading Windows) Someone please explain how I uninstall Ubuntu so I can fresh install my copy of windows

---

### Post by coffeecat on 2011-01-09
What type of Windows disc do you have, a Microsoft installation CD or a manufacturer's restore disc? If it is a Microsoft disc then a crash may or may not be to do with Linux partitions on the hard drive. A manufacturer's restore disc - depends on the manufacturer.

Boot up with the Ubuntu live CD to the live desktop. Go to System > Administration > Gparted. You can now delete all your partitions. If you have a swap partition the live CD will have automounted it, so right-click on it and choose 'swapoff' before you attempt any deletions. Remember that you have to click on 'apply' (the green tick button depending on your version of Ubuntu) after you have marked the partitions for deletion.

While you are using Gparted, it is a good idea to create one primary NTFS partition for installing Windows to, leaving unallocated space for installing Ubuntu later. This will only work reliably if you are using a Microsoft Windows disc. Manufacturer's restore discs will do their own thing.

---

### Post by lkraemer on 2011-01-09
If your Windows XP CD is an install CDR, then this should help.
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Be sure to check out their other Dual Boot articles too!

Otherwise, you may have to blow away the Ubuntu install, start with a fresh
Install of XP, then when XP is up and running, install Ubuntu.

Be sure to save any Data files, Bookmarks, and other important files that
are on the current Ubuntu install.

If you just need XP once in a while, why not install Virtualbox
(PUEL Version which has USB Support) from [www.Virtualbox.org](www.Virtualbox.org) and
then install XP in Virtualbox.  This assumes you have at least 2 Gig of RAM for
Virtualbox & XP to use.

As far as Partitions..... XP will want to be the FIRST Partition (NTFS).
Since there is a MAXIMUM of FOUR Primary Partitions on any Physical Hard
Drive, you have three available after XP is installed.  Linux requires a
minimum of TWO.  ROOT and SWAP.  But you can also have the User's /HOME
Partition which would be the Maximum.

You would boot the Ubuntu LiveCD, Run Gparted, Locate the XP Partition
(just noting it's size, location, etc), then create your System Partition /
(7-10 Gig), your /home Partition.....remainder of SPACE minus
2 Times your RAM, and then the Linux Swap, which is 2 Times your RAM.

Continue with Ubuntu Install from LiveCD.  Restore your backed up files.


lk

---

