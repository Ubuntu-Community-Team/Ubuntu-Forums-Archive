---
title: "Reinstall u14.04.1 get grub menu on select get black screen sameo sameo"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by nu2u904 on 2015-05-18
reinstalled u14.04.1 same problem displays grub menu and when I select it get a black screen no problem with live run did all was told to do: boot repair , modify grub file, no success. I thought reinstall would overwrite old grub, not so. On original install no problem until I went into suspend.

---

### Post by oldfred on 2015-05-18
If you get grub menu, then you are booting and Boot-Repair cannot usually fix issue.
Often then a driver issue and most often black screen is video related.
What video card/chip?
What brand/model system.
UEFI or BIOS install?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

