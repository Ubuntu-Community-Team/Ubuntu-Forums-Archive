---
title: "Error 15"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by pclapham on 2009-11-18
Hi --

I have a server which, because the Karmic upgrade fouled up my Samba files (another story), I reloaded Karmic cleanly.  However, when I try to boot Karmic I get the dreaded Error 15.  Looking at the grub.cfg file, it's clear that the UUID for the disk on which the boot sector is located is the same /dev/sdc1 that is reported by blkid.  So it should work, shouldn't it?  But it doesn't.  I've tried the "rescue broken system" reload of the boot sector, but to no avail.  I've also read the community documentation about how to upgrade to Grub2, but they don't help.  Is there a way to upgrade back to plain old Grub?  Or is it possible to get Grub2 to work?

Thanks for your help

---

### Post by dstew on 2009-11-18
You should be able to boot Karmic with either grub legacy (plain old grub) or grub 2. If you want to use grub legacy, you need to be sure it is a version that supports ext4, if your server has that file system on it. I think grub 0.97-29ubuntu47 and more recent will support ext4. There are packages for both [grub]("http://packages.ubuntu.com/karmic/grub") and [grub2]("http://packages.ubuntu.com/karmic/grub2") in the Karmic repositories. The grub2 package in the link here is a dummy that points to the real package, named [grub-pc]("http://packages.ubuntu.com/karmic/grub-pc").

---

