---
title: "Error installing shim-signed"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by fballem on 2013-11-16
Hi,

I've been using Ubuntu for a number of years. I have a package that is in the update manager called Secure Boot chain-loader Bootloader (Microsoft-signed binary) that is in the installation list. (currently using ubuntu 12.04 64-bit)

I have included the text of the message that I get when I select the Details. This is way beyond my knowledge, so any help would be much appreciated. I have an HP ENVY h8-1410. I am not running Window, but I am using UEFI. Ubuntu installed on it correctly. If you need any more information, please let me know what you need and how to obtain it.

Many thanks,


```
installArchives() failed: Setting up shim-signed (1.5~12.04.1+0.4-0ubuntu4) ...
Unrecognized option `--target=x86_64-efi'
Usage: grub-install [OPTION] [install_device]
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --boot-directory=DIR    install GRUB images under the directory DIR/grub
                          instead of the /boot/grub directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkrelpath=FILE   use FILE as grub-mkrelpath
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --allow-floppy          Make the drive also bootable as floppy 
                          (default for fdX devices). May break on some BIOSes.
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
   --removable             the installation device is removable
   --bootloader-id=ID      the ID of bootloader.
   --uefi-secure-boot      install an image usable with UEFI Secure Boot
                           (only available if the grub-efi-amd64-signed
                           package is installed)
   --no-uefi-secure-boot   do not install an image usable with UEFI Secure
                           Boot, even if the system was currently started
                           using it

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub, and uses grub-setup
to install grub into the boot sector.

Setting up shim-signed (1.5~12.04.1+0.4-0ubuntu4) ...
Unrecognized option `--target=x86_64-efi'
Usage: grub-install [OPTION] [install_device]
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --boot-directory=DIR    install GRUB images under the directory DIR/grub
                          instead of the /boot/grub directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkrelpath=FILE   use FILE as grub-mkrelpath
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --allow-floppy          Make the drive also bootable as floppy 
                          (default for fdX devices). May break on some BIOSes.
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected

```

---

### Post by ubfan1 on 2013-11-16
Not every UEFI machine has the Secure Boot capability.  Check your BIOS/UEFI settings, if present, there must be a way to disable/enable it.  Your error is from running the wrong grub-install, not the grub-efi version.  The only reason to use secure boot is if you are dual booting with Windows 8 which requires it (and not even all machines with W8 require it).  Be happy you apparently don't need it.  shim is the program Microsoft signed, which allows it to run when secure boot is on.  All it does is run a signed by Canonical grub, which then can run signed or unsigned linux kernels.

---

### Post by fballem on 2013-11-17
What is the right grub-install. If I disable secure boot, then ubuntu doesn't boot and I'd have to reinstall from scratch, which I would prefer to not do.

Thanks,

---

