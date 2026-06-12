---
title: "Install on EFI disk with Windows 7"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by daibhaid on 2015-07-06
I have a 3tb drive in which I have split partitions to accommodate both Windows and Ubuntu, however, I cannot get WUBI to play with my EFI drive. It kicks back an error message essentially saying that WUBI cannot access EFI drives. Help!

---

### Post by oldfred on 2015-07-06
Wubi has been discontinued as it does not work with gpt. And all new Windows 8 systems are UEFI with gpt.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

    You also may have to modify Windows installer slightly on USB flash drive. It normally defaults to BIOS boots.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

For Ubuntu add additional partitions with gparted or installer.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Windows 8 instructions on installing may generally be better than most Windows 7 install instructions as Windows 7 usually is BIOS install. Only real difference in UEFI install with 7 is that 7 has no secure boot, nor fast startup. But still make sure you do not use hibernation.
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by hakuna_matata on 2015-07-06
> **daibhaid said:**
> I have a 3tb drive in which I have split partitions to accommodate both Windows and Ubuntu, however, I cannot get WUBI to play with my EFI drive.
IMHO if you can split partitions to create own partitions for Ubuntu, there is no need for Wubi. Maybe, Wubi raises false expectations.
> **daibhaid said:**
> It kicks back an error message essentially saying that WUBI cannot access EFI drives.
The error message of Wubi means that you use Windows in EFI mode. It does not mean that you cannot install Ubuntu in EFI mode. But you should not use Wubi because there are known problems by using Wubi and Windows Boot Manager in EFI mode.

edit: FYI: An EFI drive (partition of a device with GPT) itself is not the  problem for Wubi. The used boot loaders Windows Boot Manager, GRUB4DOS and GRUB2 support GPT. The problem is that the booting method of the official Wubi versions needs old BIOS mode because it uses a virtual MBR to boot (file wubildr.mbr). But: In UEFI mode a MBR is not used for booting. So Windows Boot Manager should switch from EFI mode to BIOS mode. Unfortunately, in most cases that does not work and you get an error message about wubildr.mbr. 

There are workaraounds for this issue but as I wrote above IMHO there is no need for a workaround if a standard install without Wubi works ootb.

---

