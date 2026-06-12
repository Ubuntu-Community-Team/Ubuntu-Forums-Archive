---
title: "Grub bootloader stops boot from USB"
date: 2015-10-18
forum: Installation &amp; Upgrades
---

### Post by AJ_Wasek on 2015-10-18
Used uniserval usb to make a start up image of Ubuntu to my usb stick. Once I place it inside of the laptop I wish to install it on, I reboot the laptop. It doesn't try to popup an install screen or anything. Just says, Welcome to GRUB and it shows my previous installation of Linux (which btw my file system is completely corrupt. I can only get into rootfs with a MINIMUM amount of commands)  I'm basically trying to boot from usb to replace everything that was on my previous partitions. I want a fresh clean install of Ubuntu through my usb stick, however this grub loader is blocking it! My system is UEFI Boot from Usb is loaded in bios and secure boot is disabled. I've installed previous distro before with USB so I know that i can make it work. Grub just seems to be in the way this time

---

### Post by oldfred on 2015-10-18
Either BIOS or UEFI boot devices in order set in UEFI/BIOS. 
So if flash drive is selected, but not correctly configured, it just defaults to next in boot order or your hard drive (probably).

So either not selecting UEFI:flash drive entry or flash drive not seen by UEFI as a bootable device.

If you turned on Secure boot in UEFI, you may have to specifically allow USB boot. You may need to both turn off Secure boot and allow USB boot. 
If you updated UEFI from vendor it resets to defaults and then you have to go back into UEFI and change all the settings you changed before.

---

