---
title: "dual boot installation stuck because cannot mount /windows"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by nlz on 2008-10-16
I tried to install a dual boot on a friend's computer. He has XP. But when I tried to add XP in the partitioning menu as a nfts drive mounted as /windows it gives me the error:

attempt to mount a file system with type NTFS in SCSI1 (0,0,0), partition #1 (sda) at /windows failed.

What can I do to overcome this problem?

---

### Post by qwertymodo on 2008-10-16
Wait, you're trying to mount windows from inside linux?  Shouldn't you just install Windows to that partition from the Windows disc?

[Edit] Didn't read carefully enough, XP is installed first.  Check out this link

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1")

---

### Post by zvacet on 2008-10-16
You don´t need to add anything.Gparted should recognize windows and free space.You will install Ubuntu on free space and grun will recognizr Windows so you will be able to boot in it.You can read [this.]("http://psychocats.s465.sureserver.com/ubuntu/dualboot")

---

