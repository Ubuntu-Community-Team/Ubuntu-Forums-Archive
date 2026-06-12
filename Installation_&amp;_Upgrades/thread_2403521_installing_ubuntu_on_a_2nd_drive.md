---
title: "installing ubuntu on a 2nd drive"
date: 2018-10-12
forum: Installation &amp; Upgrades
---

### Post by merlin2049er2 on 2018-10-12
Hi, I'd like to install ubuntu onto a second ssd drive, but I'd like to use the bios boot menu to select the drive to boot to.
I don't want a boot manager (grub) installed, is this possible?  If so, how is it done?  I tried installing on a secondary drive, but it failed when it attempted to install grub on the same drive.

Thanks,
Joe

---

### Post by oldfred on 2018-10-12
UEFI or BIOS?

You have to install grub as it is both a boot manager (menu) and boot loader. But you can hide menu once installed.

If BIOS, you just install grub to MBR of Ubuntu drive.
If UEFI bit more complex, but easiest is to disconnect all other drives.

But if not disconnecting drive, you have to partition in advance with an ESP - efi system partition. But grub only installs to first drive's  ESP. You then have to doe some reconfiguration.

Post this:
sudo parted -l

What brand/model system?
What video card/chip?

---

### Post by merlin2049er2 on 2018-10-15
I tried creating a efi partition of 100mb, and tried to install the bootloader (grub) into it. no luck it says grub can't been installed.

---

### Post by sudodus on 2018-10-15
If you can disconnect (or unplug) the first drive, it will be easy to install Ubuntu into the second drive. And this way the two drives are independent and you can decide which drive to boot from via an UEFI/BIOS boot menu.

This can be done both in UEFI mode and BIOS mode, and it is a good alternative particularly in UEFI mode because otherwise the installer 'wants to' but the bootloader, the EFI system partition with its files into the first drive.

See this link with detailed instructions, [How do I install Ubuntu to a USB key? (without using Startup Disk Creator)](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312)

---

### Post by C.S.Cameron on 2018-10-16
Use mkusb as a base for a full install, it has little problem with BIOS or UEFI.
A recent post: [https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers](https://askubuntu.com/questions/1083330/how-to-make-an-usb-ubuntu-installation-more-compatible-with-different-computers)

---

