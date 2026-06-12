---
title: "Move GRUB from one MBR to another"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by d5xtgr on 2010-08-28
Hi

I recently installed Ubuntu Lucid Lynx for a friend; for non-technical reasons, the installation had to be to a USB drive instead of writing to the internal hard disk.  After reading some online literature on the subject recently, I suspect that the GRUB may be on the internal hard disk MBR instead of the MBR for my USB drive.  How can I move the GRUB to another MBR without completely reinstalling it?

Thanks

---

### Post by Mark Phelps on 2010-08-29
> **d5xtgr said:**
> How can I move the GRUB to another MBR without completely reinstalling it?

Thanks

I don't believe this is possible -- because you would have to replace the MBR of the internal drive with an MBR that you don't have.

So basically, you will have to:
1) install GRUB to the external drive MBR
2) replace the MBR of the internal drive

That accomplishes the same, but it's not "moving" GRUB.

---

### Post by oldfred on 2010-08-29
More detail on how to do Mark Phelp's recommendation:

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

