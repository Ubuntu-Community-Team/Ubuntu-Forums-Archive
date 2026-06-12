---
title: "[SOLVED] Removing Edgy from Triple Boot (WinXP, Edgy, Feisty)"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by matthewartz on 2007-06-14
I have a triple boot system with WinXP, Edgy, & Feisty.  I made a conscious decision to keep Edgy as a separate boot (instead of upgrading) for a variety of reasons.    

Now that I'm a couple of months into using Feisty, I find that I'm using it pretty much exclusively and would like to free up the space being used by Edgy for use by Feisty.  I have a boot version of gparted that I'm fine using, but I assume a simple delete of the Edgy partitions would mess up the boot record.

Can someone offer me suggestions on the most effective way of removing the Edgy install?  Is this as simple as editing the grub menu (I'm guessing that's a resounding NO...)?

One caveat which may or may not be relevant: both are 64-bit installs.  System data available if it's relevant.

(BTW, I've already compacted the Edgy partition down to about the minimum to leave it running.  I'd really like the extra 4gb back.)

THANKS!  :D

P.S.  Feisty is great!!

---

### Post by 67GTA on 2007-06-15
Which OS is grub booting from?

---

### Post by matthewartz on 2007-06-16
WinXP was the original OS.  Ubuntu 7.04 is the default boot out of Grub.

---

### Post by Pumalite on 2007-06-16
> **matthewartz said:**
> WinXP was the original OS.  Ubuntu 7.04 is the default boot out of Grub.

That's not the question they asked you. The question is what OS did you install last and more important: where did you install GRUB; MBR or the root of the drive?

---

### Post by 67GTA on 2007-06-16
As long as grub does not boot from the Edgy partition, you can just use Gparted to delete it. Then remove Edgy from /boot/grub/menu.lst. You will never know it was there unless it is listed in /etc/fstab for automounting.

---

### Post by floke on 2007-06-16
Yep. If you installed Feisty last then go ahead and delete Edgy, then remove the menu.lst entry.

---

### Post by matthewartz on 2007-06-17
Thank you!  :D

---

