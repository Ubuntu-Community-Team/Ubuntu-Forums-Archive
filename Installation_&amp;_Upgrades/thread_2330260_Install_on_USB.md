---
title: "Install on USB"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by Tony_Palermo on 2016-07-09
[COLOR=#222222][FONT=Verdana]Every time I install Ubuntu to a USB 3.0 stick it installs the boot loader to my internal hard drive.  I have double checked and reinstalled made sure I told it to install the boot loader to the USB partition.  Can someone please give me some advice on why when I tell it to install to a USB it installs the boot loader to the internal hard drive?  I will take any help I can get at this point.  I've tried install it about 4 times and i'm stick of trying to figure it out.  I just wanted to make a stick so if I go to a friends house or family I can take all my files with me.  I don't know if this is even an option at this point.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Thanks,[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]Tony[/FONT][/COLOR]

---

### Post by ubfan1 on 2016-07-09
That's bug 1173457.  The installer always puts the Ubuntu bootloaders on the first disk, usually sda.  But the good news is that the bootloaders are just files, you can make a 300M partition on the USB, put a FAT filesystem on it, and copy the files from the hard disk's EFI.  One other bug, the USB is a "removable media", so the default bootloader used is actually in /EFI/Boot/bootx64.efi (assuming 64 bit architecture).  To fix that, just copy grubx64.efi and shimx64.efi from /EFI/ubuntu to /EFI/Boot and then rename /EFI/Boot/shimx64.efi to /EFI/Boot/bootx64.efi.  Save the old bootx64.efi if you want, it's just a copy of the Windows bootloader.  Those fixes will allow the USB to boot on a UEFI system.  Since it has nothing in the MBR, it will not boot on a legacy system.Setting it up to boot both ways is possible, takes another 2M partition labeled GRUB_BIOS (?), and another grub-pc package install, but leave that out as perhaps not needed.

---

### Post by sudodus on 2016-07-10
You can get a portable installed Ubuntu mini system that can boot in both UEFI and BIOS mode. After installing the system, you can install your favourite desktop environment or only a simple window manager and your favourite program packages. See the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

If your system must work in a 32-bit computer, the following link offers an alternative,

[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](http://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300)

---

