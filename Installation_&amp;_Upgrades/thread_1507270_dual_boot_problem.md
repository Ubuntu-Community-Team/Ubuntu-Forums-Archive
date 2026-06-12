---
title: "dual boot problem"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by fidelfloris on 2010-06-11
I have a problem,

I upgraded Ubuntu to 10.04
now Vista does not work anymore.

There is an entry in the grub menu but if I choose Vista the grub loads itself again and I can only choose Ubuntu.

I have got an Ultimate boot cd, and I can get to the recovery of Vista.
But if i choose to recover I lose al my data.

Has anybody got an solution?

Greetings Fidel

---

### Post by cbecker78 on 2010-06-11
Why do you say if you use recovery, you loose all of your data?  That is not the way it is supposed to work...  By I would back up all data on your Vista partition... then try the recovery.  First, just try "fix mbr" option, and that will probably get it working again.

---

### Post by oldfred on 2010-06-11
When you say upgrade did you install grub to all the partitions (the instructions said drives) which everyone is doing. Windows has essential boot data in the Vista partition boot sector.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

