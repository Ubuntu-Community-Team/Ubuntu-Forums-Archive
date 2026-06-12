---
title: "Installer not seeing drives on ICH10R"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by Jericon on 2008-07-16
I am trying to install the current version of Ubuntu on my newly built computer.  I have an Asus Maximus II Formula motherboard using a ICH10R SATA controller.  The installation sees no devices for hard drives.  I know that they work as I have been able to install Windows XP x64 without issues.  I also have attempted the CentOS 5.2 installation DVD and it does see the drives as well.

Using the Alt installation disk image, I am asked to select a driver for the controller.

Does anyone have any idea what driver to use?  I'd rather not have to go down the list of all of the drivers to find the correct one.

Thanks in advance!

---

### Post by logos34 on 2008-07-17
Did you change the default Bios settings (i.e. sata section)?

---

### Post by justmoon on 2008-08-14
Had the same problem - selecting ide_generic in the list solved it for me.

---

