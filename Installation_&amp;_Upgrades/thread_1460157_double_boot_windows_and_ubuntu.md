---
title: "double boot windows and ubuntu"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by Omar_Gangtux on 2010-04-22
i have ubuntu and i need to install windows. is there a way of doing that without having to install windows completely first?

---

### Post by 1999panos on 2010-04-22
Read the instructions in this site: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) 

[CENTER]**1999panos**
[/CENTER]

---

### Post by oldfred on 2010-04-22
The key part will be windows will install its boot loader to the MBR. You then have to reinstall grub to the MBR and run sudo update-grub. Grub legacy often finds windows but sometimes we have to manually add an entry to menu.lst. Grub2 with Karmic almost always finds working windows and other operating systems.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

