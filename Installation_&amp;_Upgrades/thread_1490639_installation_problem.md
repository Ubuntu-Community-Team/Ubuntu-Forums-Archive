---
title: "installation problem"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by eldergnome on 2010-05-22
Trying to install dual boot.  I previously had Ubuntu installed and uninstalled it so I could set up a dual boot.  The dual boot was so I could take some time to learn and set up backups of passwords etc.  When I tried to boot after dual installing I received an error message that Windows was not present followed by a grub prompt.  I reinstalled Windows XP SP3 and want to try setting up the dual boot again.  Other than simply trying again, are there steps I need to try before putting in the Ubuntu disk?

---

### Post by SlidingHorn on 2010-05-22
Give this a read before you try it...should give you an understanding of what to do and what kinds of issues you may encounter:  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by darkod on 2010-05-22
I hope you didn't let XP take the whole disk. Since you were already planning dual boot, you probably left unallocated space for ubuntu.

If you did, just start the installer and use the Use Largest Available Free space option. It will install it into the unallocated space. Or use Manual Partitioning if you want to.

If you let XP take the whole disk, you need to shrink it first and XP doesn't have built in tools for that. If it's a new XP install it's probably better to reinstall it but this time give it a smaller partition, only the size you want allocated to XP.

If you need to shrink it, boot ubuntu into live mode, open Gparted and shrink XP. Don't start installing ubuntu yet!!!

Boot XP few times to do its disk checks. Note that the shrink might corrupt it, XP is problematic about that.

Once the shrink is done, the above aplies as if you left unallocated space for ubuntu.

---

