---
title: "Installed via Wubi, Errors After Restart"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by WinterXL on 2011-04-10
Hello,

I installed via Wubi.  Reboot, and select Ubuntu.  The purplish Ubuntu start screen appears for a moment, then something similar to this (copied from a Japanese site, but it should be the same as what I got, judging from memory):

> BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(Initramfs) /scripts/casper-premount/20iso_scan: line 46: can't open /dev/sr0: Nomedium found

Could not find the ISO /ubuntu/install/ubuntu-10.10-desktop-amd64.iso
This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, 
an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this,
simply reboot info Windows, let it fully start, log in, run 'check / r', then gracefully shut down and reboot back info Windows.
After this you should be able to reboot again and resume the installation.

Why is it accessing SR0?  I burned an image for giggles and it still says no media.  And as far as I could tell there is no /ubuntu/install there, much less an ISO.

WTF?

---

