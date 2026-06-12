---
title: "Can not boot without external drive plugged in"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by bob-b on 2011-01-16
I have installed ubuntu 10.10 on and external usb drive and now my computer which runs XP will not boot unless the external drive is connected and on.  Can I by pass this situation or do I have to uninstall ubuntu altogether and start over?

---

### Post by kansasnoob on 2011-01-16
Look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by C.S.Cameron on 2011-01-16
If you have the XP install CD, boot from it and run the Emergency Repair Console and type "fixmbr".

This can also be fixed with lilo.

Next time you install to USB unplug your internal HDD or use manual partitioning and select the USB drive for install of the bootloader.

---

### Post by bob-b on 2011-01-16
Yes, thanks to all.  Am new at this and must have typed in something wrong because I couldn't access my external drive after, but I decided to format the drive and re-install with wubi.  All is working well now.  Thanks again

---

