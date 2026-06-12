---
title: "grub2 error after install (dual-boot Win8 / MythBuntu)"
date: 2013-10-11
forum: Installation &amp; Upgrades
---

### Post by justpaul on 2013-10-11
After installing mythbuntu, I am getting the following error on boot:

error: unknown filesystem.
grub rescue>

The paste from boot-repair is here:

[http://paste.ubuntu.com/6224777/]("http://paste.ubuntu.com/6224777/")

The only thing I can think that would make this install out-of-the-norm is that the drive (and there's only one hard drive) is on a Siig UltraATA 133 PCI - Ultra ATA - Controller.

Any ideas/thoughts/suggestions would be most welcome. Thanks!

---

### Post by justpaul on 2013-10-11
results of ls:
(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (cd0)

ls (hd0,msdos1)/
error: unknown filesystem.

ls (hd0,msdos2)/
error: unknown filesystem.

ls (hd0,msdos3)/
error: unknown filesystem.

---

