---
title: "Problem with installing windows 7 after installing Ubuntu 10.10"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by Kill_steR on 2011-02-27
Hi,
im new in this Ubuntu field.before this my computer operate with Windows 7 and yesterday i try install ubuntu 1010 in my system but after install it for the 3rd times i cant boot in to my windows neither do ubuntu....so i try it for the 4th times and i choose to wipe off my first partition which have the windows in it. so i manage to install ubuntu now but the problems is i cant get back to my windows because i cant install it from the cd/dvd....please help me from step by step how to install windows 7 after install ubuntu. i already do a search at google but nothing happen to my system so far.:confused:

---

### Post by Dutch70 on 2011-02-27
You need to install windows first.

pick one...

[http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/]("http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/")

[http://www.wonderhowto.com/how-to-dual-boot-ubuntu-10-10-and-windows-7-side-by-side-0123943/]("http://www.wonderhowto.com/how-to-dual-boot-ubuntu-10-10-and-windows-7-side-by-side-0123943/")

---

### Post by oldfred on 2011-02-27
Are you installing from a full install CD/DVD or a recovery DVD? If a full install you need a primary NTFS partition with the boot flag. If it is a recovery disk it will just overwrite entire drive.

Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
chroot version:
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

