---
title: "Ubuntu Partition not Identified"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by drmsucks on 2007-05-14
Just installed 7.04 on a drive that has Win Vista installed.  The physical drive is 320 GB and was partitioned at Vista install with 100 GB partition (G drive) and 220 GB unallocated space.  Vista is installed on the 100 GB space.  During the Ubuntu install, I directed the installation to the unallocated space to install Ubuntu.  Everything appears to have gone fine but I don't get a boot option for Ubuntu - just Vista. (Using the Vista bootloader.)   The space formatted by the Ubuntu install does not show a Windows drive letter.  Booting from the Ubuntu disk, it shows the Ubuntu partition and the Ubuntu swap file.  How do I get Ubuntu as a boot option?  Thanks.

---

### Post by Jiroo on 2007-05-14
I don't know the Windows bootloader, but I'm almost sure that it just recognises windows OS's. You have to use a bootloader allocated on a linux partition. At the end of the installation questions (as far as I remember), you're asked if you want grub to be installed, say yes. That's the easy way, installing it manually is a bit more difficult. If you want to try it,[ this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation") might help you.

By default, Windows won't recognise any partition on your disks in a different file system from NTFS and FAT(32). You need a program such as [www.fs-driver.org]("www.fs-driver.org") in order to do that.

---

