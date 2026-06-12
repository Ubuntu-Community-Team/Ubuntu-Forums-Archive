---
title: "Install with XFS"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by dsk3801 on 2008-05-08
I'm installing Ubuntu on a dual-boot laptop.  The first partition is for Windows.  I want to install Ubuntu on the second partition using the XFS file system, but when I try, it says that Grub may not work correctly with it and I should use Lilo instead.  Unfortunately, there's no option to use Lilo during the installation.  Can I just not use XFS because of this?  If I do, will it bork my install so that I can't boot up?

Your help is appreciated!

---

### Post by Archmage on 2008-05-08
Sorry, did you try to install it anyway? But since XFS isn't journaling this would be a little risky.

If you have enough space on your harddrive, than I would suggest to use a root partition in ext3 and a home partition in XFS.

---

### Post by articpenguin on 2008-05-08
Xfs is a journalled filesystem which journals only metadata.

---

