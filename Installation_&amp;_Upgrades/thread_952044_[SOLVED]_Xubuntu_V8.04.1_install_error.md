---
title: "[SOLVED] Xubuntu V8.04.1 install error"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by Kernel Software on 2008-10-18
I'm trying to install Xubuntu V8.04.1 onto an older machine from a CD.  The disc boots, install runs for a minute, and then stops at an (initramfs) prompt.  I've displayed the casper.log and it shows the following error:

Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

The same thing occurs when I just try to run Xubuntu.  I'm a Linux newbie and have no idea where to go from here.  Can anybody give me some pointers?  Thanks!

Machine specs:

Gigabyte GA-GVX7-4X main board
Pentium III 800 MHz processor
128 MB 133 MHz SDRAM
Floppy, CDROM, 20 GB hard drive
ATI AGP 2x 8 MB
3Com 3C905B NIC

---

### Post by Kernel Software on 2008-10-21
I discovered the problem.  Apparently some older CDROM drives did not support reading from CDR media.  We can boot from the media and read the media, but not reliably.  We found four other drives (same exact model) with the same issue.  Replacing the drives allowed the installs to complete without error.

---

