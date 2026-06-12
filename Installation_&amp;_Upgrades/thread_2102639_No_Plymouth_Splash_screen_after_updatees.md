---
title: "No Plymouth Splash screen after updatees"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Rifester on 2013-01-07
I think something happened with updates to Grub, but I am not sure.   I no longer have a Plymouth splash screen at boot or shutdown.   My wife doesn't like to see all of the boot text...   Any ideas?   Most of the answers out there seem to related to Nvidia cards which I don't have.   I am running 12.04 64 bit.   Appreciate the help!


mark@Ubuntu-Lenovo:~$ lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)

---

### Post by Rifester on 2013-01-07
I think I found the cause:  To fix a brightness control issue after install, I had to change this line in /boot/grub/grub.cfg from 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor" 

This fixes my brightness controls but does not give me a Plymouth splash screen any longer, is there any way to have both function?  I am not sure how to make them both work...

Solved by changing to GRUB_CMDLINE_LINUX_DEFAULT="acpi_backlight=vendor quiet splash"

---

