---
title: "Modify Booting sequence to be able to see and access both Ubuntu 14.04 &amp; Windows 7"
date: 2016-01-20
forum: Installation &amp; Upgrades
---

### Post by ciller2 on 2016-01-20
[SIZE=3][FONT=arial]Hi!!

I just installed a version of Ubuntu 14.04 alongside with a Windows 7 installation and I wasn't able to configure it as to see them both while booting. I was planning to modify the GRUB booting file, but I had to leave the country and I can only make it through ssh + X11vnc...

So far, I used the "boot-repair" tool and it produces the following message when clicking on **suggested repair**: 

*"The current session is in Legacy mode. Please reboot the computer, and use this software in as EFI session. This will enable this feature. For example, use a live-usb of Boot-Repair-Disk-64bit."*

Here's a link to my installation details: [paste.ubuntu.com/14581552/]("http://paste.ubuntu.com/14581552/")

The main problem is that I can't turn off the machine, as I will lose control over it. I guess I can modify everything from within the current Linux session, but I'm not sure how. Does anybody have any recommendation or is familiar on how to modify Grub booting file sequence?

Thanks in advance for your help :D!!
[/FONT][/SIZE]

---

### Post by oldfred on 2016-01-20
You have installed in mixed boot modes.
Windows only boots in UEFI boot mode from gpt partitioned drives.
Ubuntu can be installed in BIOS boot or UEFI boot from gpt partitioned drives if you have correct supporting partitions. 
UEFI mode needs the ESP - efi system partition and BIOS need the bios_grub partition.
You show grub installed to MBR, but no bios_grub partition. 
It may boot but is not really installed in BIOS mode correctly without bios_grub partition.

Most of the fixes require a reboot and/or UEFI settings changes which requires a reboot.

You may be able to uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI), but not sure if system will not just try to boot in BIOS mode and then that will just then hang, as install is now UEFI. And in UEFI you have to change setting to UEFI first, CSM off or similar settings in UEFI.

Normally I would not suggest erasing grub in MBR (with dd), but if you do want to convert to UEFI boot to be able to boot Windows, you may be able to erase MBR, and UEFI may then see no BIOS boot mode and switch to UEFI. Some try UEFI, then BIOS and may work. But if grub in BIOS mode is in MBR, then once BIOS turns over boot to that grub, then you are trapped with an unbootable system, until you change UEFI settings.

Probably best just to leave Ubuntu in BIOS mode, until you get back to system or have something there to push reset.

Boot-Repair's full uninstall/reinstall of grub in UEFI mode actually just installs grub-pc and reinstalls grub-efi-amd64. You probably can just do that from command line. And grub's efi install will add an ubuntu entry to UEFI boot as default. But some brands/model system will not boot Ubuntu and only boot Windows. Those then require you to boot live installer and do a work around. Again multiple reboots probably required. So what brand system can make it difficult to remotely maintain.

---

