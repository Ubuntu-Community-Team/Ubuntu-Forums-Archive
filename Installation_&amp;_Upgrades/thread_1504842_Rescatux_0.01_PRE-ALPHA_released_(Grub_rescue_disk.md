---
title: "Rescatux 0.01 PRE-ALPHA released (Grub rescue disk) Please test"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by adrian15 on 2010-06-08
[Download ISO  0.01 (357 Megabytes)]("http://supergrubdisk.org/rescatux/rescatux_cdrom_2010_06_07.iso")

[Download ISO 0.01 MD5 Checksum]("http://supergrubdisk.org/rescatux/rescatux_cdrom_2010_06_07.iso.md5")

[Other downloads]("http://supergrubdisk.org/rescatux/")

** Please read carefully the following lines:**

Features (or non-features)

    [LIST]
[*]It only has one option: Install grub into the mbr
[*]Works on Debian Stable install
[*]Might not work on some Fedora systems because of incorrect fstab parsing
[*]Not tested in Ubuntu.
[*]If you have multiple hard disks you are not asked where do you want Grub to be installed... **it installs it into the same hard disk as the partition where Grub system is without asking if you want to do so**.
[*]There is not integrated help yet.
[/LIST]
 

No bug tracking system has been set up yet so you can use the [Rescatux forum for reporting bugs]("http://rescatux.berlios.de/forum/").

As long it is a PRE-ALPHA I think it scares too many people out there, but I need someone to test it in Ubuntu. So if you know how to fix boot after a grub reinstall, go ahead!

Basically you will find a wizard that will help you to reinstall Grub into your hard disk MBR when it is overwritten (e.g. by windows). It only works with one hard disk, well, it might work with various hard disks if the GNU/Linux hard disk is the first one.

You can use Rescatux forum or you can answer here in this thread with your tests, thoughts or whatever you want to.

adrian15

---

