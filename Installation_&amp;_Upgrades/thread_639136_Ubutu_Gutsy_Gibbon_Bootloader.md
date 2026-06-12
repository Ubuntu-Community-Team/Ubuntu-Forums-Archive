---
title: "Ubutu Gutsy Gibbon Bootloader"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by jmasta on 2007-12-12
I have recently installed Ubuntu Gusty Gibbon, and i previously had PCLinuxOS. now when i start up ubuntu i have no choice to start pclinuxos. How can i make it so i can choose between the startup for the OSs?

---

### Post by confused57 on 2007-12-12
> **jmasta said:**
> I have recently installed Ubuntu Gusty Gibbon, and i previously had PCLinuxOS. now when i start up ubuntu i have no choice to start pclinuxos. How can i make it so i can choose between the startup for the OSs?
A configfile entry should work for booting PCLinuxOS:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
add the PCLinuxOS entry to the very bottom of the menu.lst file, then quit & save

---

