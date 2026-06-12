---
title: "Convert USB stick from UEFI to legacy"
date: 2019-01-25
forum: Installation &amp; Upgrades
---

### Post by SeijiSensei on 2019-01-25
I'm really at wits end here.

I have a machine with a hard drive in legacy mode.  I want to install Kubuntu 19.04 onto it and be able to boot the Win7 partition on the drive as well.

I'm trying to force a USB stick into legacy mode.  I've used gparted on another machine to delete all the partitions on the stick and set the type to "msdos."  I then used usb-creator-kde to write the image to the drive.  When I plug it into the computer, the BIOS says its a UEFI device.  

Documentation on the Internet about converting from UEFI to legacy is sparse.  Is there a good howto I can read?  

When I try to boot the device, I get a "cannot find /BOOT/EFI" error (note the caps).

The system is an ASUS M32.  I got this to work in the past with earlier versions of Ubuntu with everything in legacy mode.

---

### Post by ubfan1 on 2019-01-25
The install medias are set up to boot both legacy and UEFI -- they are FAT, have an EFI directory (with the UEFI bootloaders), and they have an MBR  for booting legacy.  How it boots is entirely dependent upon the BIOs/UEFI settings of your machine.  Those settings are pretty machine specific -- some give you a preference (UEFI before legacy, or vice versa), some allow you to select a boot mode UEFI vs CSM (?) compatibility (legacy mode).

---

### Post by oldfred on 2019-01-25
IF you have UEFI Secure Boot off, and probably allow USB boot settings, you then should get two boot options in UEFI for USB flash drive.
One is clearly UEFI as UEFI:drive where drive is name or label of flash drive. Other boot option should just be drive and will be a BIOS boot.

If UEFI settings are correct, then flash drive may not be correctly configured. 
But most programs create the standard dual boot image on a flash drive.
Some use dd or dd under the hood to create the hybrid DVD/flash configuration. 
Others extract files and install syslinux as BIOS boot loader. Ubuntu files already have the /EFI/Boot/bootx64.efi for UEFI boot, so both boot modes are available.

---

### Post by SeijiSensei on 2019-01-26
Thanks so much!

For some reason Secure Boot was re-enabled. I turned it off.

I also zeroed out the USB device with dd then created the installation image again.

It wasn't immediately obvious in the BIOS where the legacy interface to the device was.  Even with Secure Boot set to "Other OS," the BIOS still showed just a UEFI option in the list of boot devices.  Searching around I discovered another option that let me select the device in legacy mode.

Now I have everything back and running again, even Windows.

---

