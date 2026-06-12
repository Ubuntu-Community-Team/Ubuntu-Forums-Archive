---
title: "How do I trim the Grub boot menu?"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by jmlynn on 2009-12-27
Hi,

My Grub boot menu has two set of Ubuntu menus (normal boot and recovery), memory test and Windows Vista boot.  It was supposed to be dual boot, but my first Ubuntu installation failed right after installation, so I reinstalled it and reuse the same partition.

How do I edit and get rid of the duplicated Ubuntu boot menu items from Grub?

Thanks for any help!

Jeff

---

### Post by raymondh on 2009-12-27
> **jmlynn said:**
> Hi,

My Grub boot menu has two set of Ubuntu menus (normal boot and recovery), memory test and Windows Vista boot.  It was supposed to be dual boot, but my first Ubuntu installation failed right after installation, so I reinstalled it and reuse the same partition.

How do I edit and get rid of the duplicated Ubuntu boot menu items from Grub?

Thanks for any help!

Jeff

Jeff,

What version Ubuntu are you using?  9.04 and older uses GRUB-legacy and the /boot/grub/menu.lst ... while 9.10 uses grub.cfg (GRUB2).

Also, are you referring to KERNELS (like 2.6.28.XX)?  When you reinstalled, GRUB would've re-installed as well hence deleting the 'old install' listing in the process.  If kernels, it's ok to have at least 2 (just in case the newer one borks).  I also suggest keeping recovery (for both kernel) and memtest.

If you are using GRUB-legacy, you can install (from synaptic) startupmanager.  SUM will allow you to set defaults, number of kernels to show, time, etc.  I use Ubuntu 9.04 and know SUM is stable with grub-legacy (from experience).

If you are using GRUB2, I don't know if SUM works or not/is stable or not.  You can manually edit the grub.cfg file to suit your needs.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

From DRS305:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Copy/back-up your grub.cfg file first (see community doc) ... just in case you 'mis-edit'.

Regards,

---

### Post by jmlynn on 2009-12-27
Raymond,

Thanks for your reply.  I had installed the latest release, Ubuntu 9.10.  I remember on the second reinstall, id did ask if I want to delete the existing GRUP or keeps it.  Not knowing any better, (I have been away from UNIX for over 15 years), I selected "keep", may be that is why I ended up with 2 sets of Ubunto boot entries, even though there is only one Ubunto boot image.

Guess I will try to edit the Grub.cfg (backup first) and see how it happens.  Only thing though, if I messed up, not sure how I can restore the backup version of grub.cfg, as I most likely won't be able to boot Ubuntu up again.

Any suggestion?

Jeff

---

### Post by jmlynn on 2009-12-27
I got it.  I used the System/Administration/Snaptic Package Manager to remove the extra kernel image from the Grub 2 menu and it works!

Thanks!

Jeff

---

