---
title: "Reinstall Windows"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by um_goblue on 2011-10-23
I installed Ubuntu 10.10 last year and have been running it on my laptop.  At the time I did the install, I did an Ubuntu-only install.  Windows does not exist on my machine.  I would like to reinstall Windows XP and then run the Windows installer for Ubuntu 11.10 to create a dual-boot system.  

I tried booting from the Windows boot CD, but it gave an error message (wrong file system).  I am stuck as to how to reinstall Windows.  Ideally, I would do the following:

1) Wipe everything
2) Reinstall Windows XP
3) Run Windows Installer for Ubuntu and Install 11.10
4) Run dual-boot system

Can anyone help me with this?  Here is the output from fdisk - l


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093525

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6993    56165376   83  Linux
/dev/sda2            6993        7296     2437121   fa  Unknown

---

### Post by scania_gti on 2011-10-24
I found [solution there]("https://help.ubuntu.com/community/WindowsDualBoot").

---

### Post by subhadip_sky on 2011-10-24
Hi, you can install Windows XP after Ubuntu. Read this [post]("http://subhadipghosh.wordpress.com/2011/07/31/installing-windows-xp-after-ubuntu/").

---

