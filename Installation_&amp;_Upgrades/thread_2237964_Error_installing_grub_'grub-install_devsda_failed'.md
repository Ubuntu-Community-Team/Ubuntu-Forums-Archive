---
title: "Error installing grub 'grub-install /dev/sda failed' GUbuntu 14.04"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by Behron_Georgantas on 2014-08-05
Hey everyone! I'm new to the forums and new to Linux so please bear with me here. 

I've been trying to install Gnome onto a 32gb Leef Supra USB 3.0 flash drive and also a 32gb San Disk USB 2.0 flash drive from a live USB.
But I'm having an issue with installing Gnome 14.04 that is preventing me from installing grub. I get the error  'grub-install /dev/sda failed' This is a fatal error message and then the installer crashes.

I'm running Windows 8.1 on an Alienware m17x with 32gb of ram
I'm using a Core i7-4900MQ CPU @ 2.8 GHz processor and running a 64-bit system.

I usually split 10-12gb for my / partition then about 18-22gb for my /home partition with a 2-4gb partition for swap space.

I also tried installing other distros like Mint and have the same issue each time. 

If you need anymore information just let me know!

---

### Post by ubfan1 on 2014-08-05
Is your target USB using GPT partitioning?  Did you put an EFI partition on it?  The usual USB target install seems to frequently put the grub bootloaders onto the hard disk's EFI partition.  Happens every time I just specify /dev/sd? for the bootloader location, and seems to still happen sometimes when I specify the actual EFI partition on the target.  Anyway, just copy the files you need from the hard disk's /EFI/ubuntu directory and that usually fixes things.  When you say "sda", that is not the name I'd expect for the USB target, I usually get sda as the hard disk, sdb as the USB live media, and sdc as the target -- so any grub.cfg which gets created refers to sdc, which does not even exist after the install media is removed -- a longstanding bug, so just edit the first grub boot item, and run sudo update-grub to fix things.

---

### Post by oldfred on 2014-08-05
Some details here, you do not have to make it both.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by Behron_Georgantas on 2014-08-09
Fixed it by installing it to a computer with no hard drive in it. Thank you for your help.

---

