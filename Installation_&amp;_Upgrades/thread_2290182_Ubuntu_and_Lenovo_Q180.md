---
title: "Ubuntu and Lenovo Q180"
date: 2015-08-10
forum: Installation &amp; Upgrades
---

### Post by petrautoauto on 2015-08-10
I have a Lenovo Ideacentre Q180 and I can not install ubuntu on Q180.


What am I doing wrong?


1) Download the distribution ubuntu 64 bit (tried 14.04 LTS and 15.04)
2) I have used UNetbootin (and other usb creater) to make a bootable USB
3) I set the BIOS to boot from usb (F1->BIOS->Startup->primary boot sequence->1: usb fdd: 2: usb key: …->F10 save and exit)
4) Loading screen on a black background with a choice 1) Try Ubuntu without installing 2) Install Ubuntu ….
5) &#1057;hoose to install and simply follow the steps Installer.
6) Ubuntu says it has successfully installed and asks reboot
7) after a reboot (removing usb) BIOS writes “reboot and select proper boot device or insert boot media in selected boot device and press a key” OS does not boot


p.s.
I tried to install with a choice through F12 uefi usb,
also I tried to manually set the drive to GPT, partitions /dev/sda1 EFI (ESP) fat16/32, /dev/sda2 ext4 /, /dev/sda3 linux-swap,
also I tried to run Boot-Repair ([http://paste.ubuntu.com/12047121/](http://paste.ubuntu.com/12047121/))


how to install ubuntu on q180?




Intel Atom D2700 @ 2.3GHZ
2GB DDR3 PC3 10600 RAM
320GB Western Digital Hard Drive @ 5400RPM’s
AMD Radeon HD 6450
Lenovo N5902 Multimedia Remote with Keyboard(backlit keyboard)
10/100/1000 Realtek RTL8111//8168B Gigabit NIC
802.11 b/g/n Realtek RTL8188CE Wireless NIC
4x USB 2.0 ports(in the back)
2x USB 3.0 ports(in the front)
HDMI and VGA port
SD/SDHC/SDXC/MMC/MS/MS_Pro card reader
VESA mount

---

### Post by grahammechanical on 2015-08-10
You set the BIOS to look for an operating system on a device plugge into a USB port. Is the BIOS still looking to the USB port? Have you now set the BIOS to look for an OS on the hard drive?

Regards.

---

