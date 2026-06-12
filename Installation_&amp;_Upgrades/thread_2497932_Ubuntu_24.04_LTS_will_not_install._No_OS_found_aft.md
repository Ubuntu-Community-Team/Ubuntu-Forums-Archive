---
title: "Ubuntu 24.04 LTS will not install. No OS found after reboot"
date: 2024-05-23
forum: Installation &amp; Upgrades
---

### Post by heian on 2024-05-23
I'm trying to install Ubuntu 24.04 on a Thinkcentre Edge 71 (machine type 1578, model number D7G from 2011). 
Ubuntu 20.04 ran perfectly on it, however I remember having difficulties to install it, as this was the time beween Legacy mode and Uefi. 
(it might be I had to press F12 during boot and choose Legacy or Bios option or something) Bios date 02/14/2012.

I downloaded the ubuntu-24.04-desktop-amd64.iso file, made a bootable USB stick with Rufus (let all the options as it was) and boot from there. 
The whole boot proces I let go as suggested, with all the extra's and automatically set the partitions. After the required reboot I doesn't see the OS.

The screen after booting gives me client mac addr: and a DHCP......\

the installation file before installing looks like this:

disk setup : erase disk and install ubuntu

installation disk sda : applications: default selection

disk encryption : none

proprietry software : codecs and drivers

partitions : partition sda1 formatted as fat32 used for /boot/efi

partition sda2 : formatted as ext4 used for /

error 1962 : no operating system found

ps: I read somewhere: this drive was created by Rufus. It can boot in UEFI mode only. You are trying to boot it in Bios/Legacy mode. This will not work.

and later on; this system uses 64-bit x86 UEFI => searching for X64 EFI bootloader. Could not locate efi\boot\bootx64.efi

_Is it possible the processor is 64 bit but the sysyem has a x86 UEFI (32 bit bootloader)? _
[https://www.manua.ls/lenovo/thinkcentre-edge-71/specifications](https://www.manua.ls/lenovo/thinkcentre-edge-71/specifications)

---

### Post by ubfan1 on 2024-05-23
I had a 2011 Thinkpad which was 64 bit UEFI but not secure boot.  Use F2 to get into the settings, and ensure you select "prefer UEFI over legacy" boot, then have your disk gpt and never think about legacy again.  The default ISO boots both ways (legacy UEFI), so the way your preference is set determines the way the USB boots and installs (unless Rufus did  something to dump legacy).

---

### Post by heian on 2024-05-23
Found the solution!

The usb-stick that failed was made with Rufus. 

Then I used Ventoy to make a bootable usb-stick. Had to press F12 during the boot process to be able to select Legacy mode. 
It started in text mode, but later the graphical mode appeared and all went well.  

So much fun to have a machine from 2011 that runs an OS from 2024  ;-)

---

