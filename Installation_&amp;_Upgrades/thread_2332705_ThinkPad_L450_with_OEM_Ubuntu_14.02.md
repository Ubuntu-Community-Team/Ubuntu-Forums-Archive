---
title: "ThinkPad L450 with OEM Ubuntu 14.02"
date: 2016-08-03
forum: Installation &amp; Upgrades
---

### Post by abheet-jamwal on 2016-08-03
[COLOR=#333333][FONT=Ubuntu]while installation it gives fatal error i.e " unable to install Grub on /dev/sda2/" .[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]To fix it i have tried to create partition on hdd with Ubuntu Live session (i.e. Try Ubuntu without installing), actually i have mounted /dev/sda1/ with disks utility i.e mark * to it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]which messed up booting process,now even when i am trying to boot Ubuntu 16.01 with Usb, it open initrams console.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Can you please help me to fix this ??[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-08-03
I do not think that Grub likes being installed to a partition. If the hard drive has MBR partitioning then Grub should be installed into the Master Boot Record (MBR) of the drive.

If the hard drive has GPT partitioning and Ubuntu is being installed in EFI mode then there needs to be a efi_boot partition for the Ubuntu efi boot files. If Ubuntu is being installed in BIOS/Legacy mode then there needs to be a bios_boot partition for the Grub boot files.

Just to be clear about the situation. Does 14.04 still load? Is the Ubuntu 16.04 live session loading to initramfs console? The original situation has now been over taken by the issue of not being able to load the 16.04 live session? Is this correct? Or, is it 14.04 that is loading to an initramfs console? If this is the case then you need to enter the BIOS/UEFI utility and set the utility to boot from the USB drive.

Regards

---

