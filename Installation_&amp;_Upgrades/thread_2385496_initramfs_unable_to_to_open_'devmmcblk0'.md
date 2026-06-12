---
title: "initramfs unable to to open '/dev/mmcblk0'"
date: 2018-02-21
forum: Installation &amp; Upgrades
---

### Post by daddadlington on 2018-02-21
Hi Guys,
I am trying to install Ubuntu 17.10 Desktop onto a HP 2in1 laptop where I have already successfully installed Linux Mint via USB.
The laptop is UEFI hardware. I am using Rufus to right my Ubuntu image to my USB stick.
I pass the screen where it asks me run Live CD or Install etc and then a Ubuntu splash screen appears and then it bombs out and displays the following:

<code> 
BusyBox v1.22.1 (Ubuntu 1:1.22.0-19ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) unable to open '/dev/mmcblk0'
mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
</Code)

I have tried alot of different ways to install the image onto the USB: ISO / DD with MBR / GPT partition scheme for UEFI.
I have Google it to death and as a last resort I am writing to this forum as I don't want to give up on this as I want my beautiful Ubuntu :)
Any help or advice will be very much appreciated. 
Things I know. I definitely booting with UEFI as I done this test: [COLOR=#111111][FONT=Consolas][ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

[/FONT][/COLOR]

---

