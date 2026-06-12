---
title: "dpkg can't install kernel in a FAT32 /boot partition"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by madoka on 2005-10-13
When I first set up Ubuntu I configured the /boot partition as FAT32.  This way I can mess with GRUB under Windows.  However, when I tried to upgrade, dpkg (invoked by apt) would fail to install the new kernel (or anything that resides in /boot, such as memtest86+).  The error appears to be that dpkg tries to create a link as part of its backup process, but FAT32 doesn't support links, so the operation fails.

I've tried to install the kernel manually with the --force-all option, but it still didn't work.  Any ideas?

---

### Post by joelito on 2005-10-13
I guess that you should try to re-install and format /boot as _ext2_. There's some _ext2_ drivers for windows in the web(notice ext(2) _not_ 3)

A quick google search revealed these : 
[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)
[http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)

---

### Post by madoka on 2005-10-14
I hope bumping isn't against forum rules...

---

### Post by llamakc on 2005-10-14
Respectfully, what would you do with the grub/menu.lst while in windows? You can edit-on-the-fly any aspect of grub's boot options/settings at each individual boot.

---

