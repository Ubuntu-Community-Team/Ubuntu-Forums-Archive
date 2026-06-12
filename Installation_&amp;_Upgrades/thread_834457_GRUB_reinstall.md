---
title: "GRUB reinstall"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by simeon_lukov on 2008-06-19
Hello all,

I have Ubuntu 8.04 installed after Vista.
Once I entered into the Vista's recovery partition I could not see GRUB boot loader any more.
What could I do to reinstall GRUB without installing fresh copy of Ubunty

Thank you very much in advance

+++

---

### Post by milia on 2008-06-19
[This link should help.]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1")

---

### Post by pablopancho on 2008-06-21
If it is only a problem with MBR, the easiest way is to use supergrub disk: [www.supergrubdisk.org/]("http://www.supergrubdisk.org/")
But first of all read how/when to use this disk because it may not be your case.

---

### Post by fogcat on 2008-06-21
Supergrub has saved my **** several times after I have experimented w/my system!!

I have also used Puppylinux as a recovery tool to access grub menu.lst and rewrite whatever I wish into it.  Check your old menu.lst (backup files) if you do use puppy and see what changes have been made to it.  Then again...this may not be your problem at all.  If so I do apoligize.  Hope this helps some.

fogcat

---

