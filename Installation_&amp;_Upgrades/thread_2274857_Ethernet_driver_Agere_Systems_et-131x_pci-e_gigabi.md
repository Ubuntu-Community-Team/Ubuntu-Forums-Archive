---
title: "Ethernet driver: Agere Systems et-131x pci-e gigabit - Ubuntu 14.04"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by neb8 on 2015-04-22
I have a laptop with an Agere Systems ET-131x PCI-e gigabit Ethernet adapter.

The hardwired networking is not displayed under Network settings. A hardwired network shows up via edit networking.

I'm looking to re-install or re-initialized the driver for the ET-131x adapter. 

It appears the laptop's Ethernet ET-131x adapter is recognized by the OS but the adapter isn't initialized or there is no driver installed.

Original OS installation there was another Ethernet hardwired network adapter installed by the OS.

sudo lshw -C network

*-network UNCLAIMED
description: Ethernet controller
product: ET-131x PCI-E Ethernet Controller
vendor: LSI Corporation 
physical id: = 0
....
configuration: latency=0

It appears there may be some sort of hardware / driver conflict?

I booted using the same Ubuntu usb drive from a nearly identical laptop that has a ET-131x PCI-E Ethernet controller and Ubuntu has no problems initializing and connecting to the Internet.

Perhaps there's a hardware/driver conflict somewhere that doesn't exist on the second laptop.

---

### Post by dino99 on 2015-04-23
Looks like you should move to 15.04 which have the 3.19.x kernel dealing with that module (14.04 does not have it, and backporting is not a serious solution)
[https://lkml.org/lkml/2015/2/11/107](https://lkml.org/lkml/2015/2/11/107)

---

### Post by neb8 on 2015-04-23
Thanks for the link.  

Ubuntu 14.04, both the 64 bit and 32 bit versions were installed onto a USB drive from a desktop PC 

The 32 bit installation seems to work ok when booted from one laptop.
The 64 bit installation won't boot from either laptop.

A usb stick installation failed after each attempt from one of the laptops, neither of which have a DVD drive.

These are older rugged laptops, using an INTEL Duo T2400 1.83 GHZ  cpu which should be able to boot to a 64 bit OS, but may require a direct 64 bit installation.

I haven't tested the usb 32-bit installation extensively from either laptop, other than the conflict from one laptop, the 32 bit install seems to work ok.

  Rather than install Ubuntu separately to each PC. (two desktops and two laptops). I'm trying to create an Ubuntu installation that will work from both my desktop PCs and laptops.

When installing Ubuntu to a USB drive from a PC,  I need to unplug the PC's internal hard drive because Unbuntu want's to install dual booting which causes conflicts and problems when moving the USB drive to another computer.

---

### Post by Mark Phelps on 2015-04-23
> When installing Ubuntu to a USB drive from a PC, I need to unplug the PC's internal hard drive because Unbuntu want's to install dual booting which causes conflicts and problems when moving the USB drive to another computer. 

Actually, when Installing Ubuntu, the installer defaults to writing GRUB to the "first" drive it finds, and since an internal drive is generally ordered before external drives, that will result in GRUB NOT being written to the USB drive.

When you have only the USB drive connected, the installer will then write GRUB to that drive -- thus allowing you to use that drive in other PCs.

---

### Post by neb8 on 2015-04-23
> **Mark Phelps said:**
> Actually, when Installing Ubuntu, the installer defaults to writing GRUB to the "first" drive it finds, and since an internal drive is generally ordered before external drives, that will result in GRUB NOT being written to the USB drive.

When you have USB drive connected, the installer will then write GRUB to that drive -- thus allowing you to use that drive in other PCs.


Before installation the PC bios device boot order was changed

PC Bios

1. DVD (Unbuntu Installation DVD)
2. USB (installation Drive)
3. PC Internal hard drive (Windows) 

My previous installations If #3 exists Grub is installed on #2 USB as a dual boot for Ubuntu and Windows
  
Boot device  #3 was removed since the #2 USB drive is used on multiple machines with different hardware and configurations. I'm not sure if this step is necessary but wanted a Grub that didn't know anything about the PC's internal drive the usb drive is being connected to.

The current install the Grub dual boots either a 64 and 32 bit Ubuntu install and does not include a 3rd Windows installation from the desktop PC's internal drive.

USB drive - Partition 1 (64 bit), Partition 2 (32 bit), Parition 3 (Linux Swap)

I'll look over details for the 15.04 version and consider replacing 14.04. 

An earlier install, when Ubuntu 14.04 performed an online os service update there were problems after rebooting. So I currently have the OS automatic update feature disabled and haven't performed any OS upgrades.

---

### Post by neb8 on 2015-04-25
After installing Ubuntu Studio 15.04 32-bit, my fingerprint reader (Fingerprint GUI) won't install. The 15.04 Studio version installation lacks certain dependencies. I tried compiling a fingerprint gui driver for version 15.04 but the os install lacks the necessary development packages.

___________


  Installing the Desktop packages and libraries, the Fingerprint Gui installed ok.

Studio omits some of the packages and libraries installed with the Desktop version, required to install some applications.

To add the Desktop packages and libraries to Studio, I used the command  "  sudo apt-get install ubuntu-desktop "

[https://help.ubuntu.com/community/UbuntuStudio/FAQ](https://help.ubuntu.com/community/UbuntuStudio/FAQ)

From a Desktop installation you can add Studio packages by using the command: 

 sudo apt-get update && sudo apt-get install  ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins  ubuntustudio-graphics ubuntustudio-video

for more information: [https://help.ubuntu.com/community/Ub...0from%20Ubuntu]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu")

---

