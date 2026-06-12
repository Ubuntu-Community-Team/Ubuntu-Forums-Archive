---
title: "Live persistent usb drive"
date: 2022-10-17
forum: Installation &amp; Upgrades
---

### Post by avocado-toes on 2022-10-17
Hello, I am new to linux and am coming from windows. Right now, I wish to use a usb as both a boot drive, and persistent storage. I will use it to dual boot a windows system using UEFI, and I wan to be able to switch between to two OS's, while saving everything linux related onto the usb drive alone, since my windows ssd is encrypted (I want to keep it that way). Does anyone know if this is possible and could someone provide me with a link or tell me how to do this? Thanks!

---

### Post by grahammechanical on 2022-10-17
I have never done what you want to do. So, I can only offer ideas.

You will need two USB ports and two USB memory sticks. Burn the Ubuntu ISO image to USB stick (A). Run the Ubuntu install session and install Ubuntu on to the second USB memory stick (B) in the other USB port.

First you need to partition and format the USB stick (B). If the motherboard is modern and has UEFI and not BIOS, you will need to create an EFI System partition of 500 to 600 MB and formatted as FAT 32. The rest of the space on USB stick (B) should be partitioned and formatted as EXT4. Use the Something Else option to put Ubuntu on the EXT4 partitions but remember to make sure that the installer puts Grub boot loader into the EFI System partition of USB stick (B). Otherwise the installer will try to put Grub onto the hard drive.

I have no idea if Grub will be able to detect Windows on an encrypted drive. It could be that the EFI system partition on the Windows drive is not encrypted. So, Grub might be able to detect the Windows boot files in the EFI system partition on the Windows drive and give you an option to boot Windows as well as Ubuntu.

Remember. You must load the Ubuntu Live session in UEFI mode for Ubuntu to be installed in UEFI mode on USB stick (B).

Regards

---

