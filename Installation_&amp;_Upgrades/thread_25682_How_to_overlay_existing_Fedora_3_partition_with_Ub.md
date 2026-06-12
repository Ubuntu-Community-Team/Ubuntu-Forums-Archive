---
title: "How to overlay existing Fedora 3 partition with Ubuntu"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by bobcat on 2005-04-10
I currently have Windows XP and Fedora 3 (dual boot with GRUB) running on my box.  I installed Windows XP first and then Fedora 3.  Now, I would like to replace the Fedora 3 with Ubuntu.  Does anyone know the easiest way to accomplish this?  I was hoping that I could just put the Ubuntu installation disk in, boot up the box, and I could just install over the existing Fedora 3 partition; however, I was unable to boot from the installation disk.  Should I try to first remove the Fedora 3 partition all together with some partition tool?  What about the master boot record (MBR)?  Do I also need to rewrite the MBR (using fixmbr) before giving Ubuntu a shot.  If I need to remove the Fedora partition and rewrite the MBR, does it matter which one comes first?  Thanks!

---

### Post by jdong on 2005-04-10
As long as you can get the Ubuntu CD-ROM to boot, you don't have to do anything "extra" with other partitioning tools -- you can select to delete & recreate the partition during the installation process.

If you're unable to boot the installation disk, please double-check your BIOS boot order (CDROM before hard disk).

---

