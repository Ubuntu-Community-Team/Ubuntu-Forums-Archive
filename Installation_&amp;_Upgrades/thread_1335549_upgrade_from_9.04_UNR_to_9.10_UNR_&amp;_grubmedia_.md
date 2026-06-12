---
title: "upgrade from 9.04 UNR to 9.10 UNR &amp; grub/media errors"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by braver on 2009-11-23
I've had a great 9.04 UNR working on my Asus Eee 900 (Celeron).  When the update manager suggested to upgrade to 9.10, I wish I didn't say yes.  After many hours of downloading and installing packages, it rebooted into a Grub stage1.5 error.

While I realized the Grub has been upgraded to v2, I decided to re-install the whole thing, since I had my home on a separate ext4 partition /dev/sda2, and reinstall the system over its own partition /dev/sdb.  From the beginning, I decided to use the fast 4 GB "ASUS OB SSD" for /home, and the larger, slower 16 GB "ASUS SSD" for system.  Swap is 1 GB on /dev/sda1, for hybernate.

OK, several attempts to reformat the ext4 on /dev/sdb lead to long delays and error.  I finally chose ReiserFS for it which I had a great time with on SuSE since 7.1.  Now it started installing.

For the startup, I still have to manually ESC in bootup and choose the second entry, ASUS SSD, as it doesn't allow to sort the SSD order in the boot sequence, just USB vs IDE vs CD-ROM (and not within IDE).  Apparently IDE master/slave can't also be used to reorder the SSD drives.

Anyhow, once I picked the right device and Grub gets going, the Ubuntu circle comes, and then suddently I get a bunch of errors, all looking like PCI or media errors, with IRQ strewn around the place.  Then I get an error for devices in /etc/fstab not available, still trying. Found the Grub2 on the help wiki, uncommented the line about NOT sending UUIDs to drub.cfg, updated grub.  Still am getting those errors, for /dev/sda1.

In 9.04, I had successful hybernation into swap.  Can that be causing the /dev/sda1 errors?  What's the overall deal with 

-- messing up Grub1 upon upgrade from 9.04 UNR to 9.10 UNR via upgrade manager
-- messing up Grub2 when fresh-installing 9.10 UNR

A search shows multiple stories of torturous scrambling after upgrade to 9.10 UNR.  This raises several serious questions about this process.  If such a radical change as Grub2 upgrade was understaken, why was it done so that it causes serious failures upon uprgade from the very previous version?

Should I just downgrade from 9.10 back to 9.04 or EasyPeasy?

---

