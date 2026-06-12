---
title: "xubuntu installed does not boot"
date: 2017-09-05
forum: Installation &amp; Upgrades
---

### Post by sebsheep on 2017-09-05
Hello,

I've installed a Xubuntu 16.04.3 on my new Thinkpad T570. The install process proceed smothly, but the bios of my laptop does not seem to find the boot section.

When I switch on the computer, the laptop displays the Lenovo's splash screen, and after a short time, a boot menu where I can choose between "Hdd" and "LAN". Trying to boot on HDD results on a black screen and a few seconds later to the same boot menu (same for LAN but that is normal, my computer is not plugged to a network).

I've tried to play with UEFI secure/unsecure/legacy options in the bios, but it does not change the boot process.

I have 4 physical partitions (in that order) on a unique SSDHD:
* swap (12Go)
* / (ext4 50Go)
* /home/ (ext4 100Go)
* ntfs, flag grub_bios, 3Mo

The "grub_bios" partition is at the end because I've added this after the installation process after the advice of "repair boot". Does it matter if this partition is not at the beginning (it is not the case on the computer I'm writing this message) ?

Here is the report of "repair boot" if it helps (the software said so...) : [https://paste.ubuntu.com/25473740/](https://paste.ubuntu.com/25473740/)

Thank you for your help.
Seb

---

### Post by sebsheep on 2017-09-06
Bump

---

### Post by Bucky Ball on 2017-09-06
Looks like you've set up the drive for a UEFI install then installed in BIOS mode. Presume you're using a USB to install? When you boot to BIOS and select the boot device, do you see two options for the USB, one with 'UEFI' mentioned somewhere next to it? That is the one if you want a UEFI install.

On many machines you can also boot and hit F12. This takes you to a boot device menu where you should see the USB with UEFI options.

This is presuming you have UEFI set in your BIOS and the details of doing that would depend on your BIOS.

---

