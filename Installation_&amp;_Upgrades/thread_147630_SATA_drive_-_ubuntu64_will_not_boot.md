---
title: "SATA drive - ubuntu64 will not boot"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by nox.freak on 2006-03-20
Hello,

I am dual booting winxp/ubuntu64 on a AMD 64 system with a Segate SATA hard drive.

I installed Ubuntu64 5.10 with out any problems grub could see my winxp partition and seemed to install to the mbr. After I restart, grub dose not load and it boots right into winxp.

I tried the live CD, the live CD could see the sata partitions but would not/could not mount the Ubuntu64 partition.

any help would be grate.

Thanks,

---

### Post by dinsdale on 2006-03-21
Stumbled upon this myself.   At the end of the installation the grub installation goes after hda, instead of sda.   It assumes standard IDE hardware and not SATA.   Must've been hardcoded.   So it never updates the boot sector.

There are utility boot cds with boot managers, or the bootimage utility (freeware, google it) or other items out there that can do this.  I decided to skip the hassle in favor of just reinstalling on an IDE drive.   Instead of using hard disk boot managers, I just use the bios setup to switch drives.

---

### Post by dinsdale on 2006-03-21
Just saw this somewhere else--haven't tried it but:

"The install program will ask to load GRUB to the master boot record (MBR) of your internal hard drive (HDA). Say NO to this, and on the next screen, type in the correct path to the drive where we want to install the GRUB bootloader.

---

