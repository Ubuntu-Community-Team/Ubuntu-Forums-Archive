---
title: "Windows 10 and Ubuntu 16.04 “Xenial Xerus” - minimal - command line installation"
date: 2016-11-12
forum: Installation &amp; Upgrades
---

### Post by Xpdin on 2016-11-12
Hi,

Windows 10 has already being installed before doing the following:

  
If it possible to install [Ubuntu 16.04 LTS "Xenial Xerus"]("http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso") on HDD as minimal as possible [LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") like in here: [Windows Dual Boot together with Ubuntu 16.04 “Xenial Xerus” - minimal - command line installation]("http://askubuntu.com/questions/845475/windows-dual-boot-together-with-ubuntu-16-04-xenial-xerus-minimal-command")

 I would like only the kernel to boot in tty, and only use fvwm, no  login manager, no other environment at all, if it is possible to work like this in Dual boot with Windows 10.

First I couldn't boot the new USB Stick created [Ubuntu 16.04 LTS "Xenial Xerus"]("http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso") from [Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") in UEFI mode like I've done with a few minutes ago, just for test with the Windows 10 USB Stick.
 

I had to boot it in Legacy mode, in order for the USB Stick of Ubuntu 16.04 LTS "Xenial Xerus" to run.

  
I installed [Ubuntu 16.04 LTS "Xenial Xerus"]("http://archive.ubuntu.com/ubuntu/dists/xenial/main/installer-amd64/current/images/netboot/mini.iso") from [Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") - command line installation.

  
GRUB has been installed on ext4, dev/sdb2, ehere the root / patition is situated. 

sda was the USB Stick.

  
All done, now in UEFI starts only Windows 10 automatically, and in Legacy mode, no system to start at all.

I don't  know if I will use only the Legacy mode, will find the HDD at all(from my trying until now  in Legacy only the USB could start).

  
When I try to access from WIndows the partition where Ubuntu should, I can't access it, and it asks only for formatting it.

  
Do you consider that if I would do this with a full Lubuntu desktop + login manager (not Ubuntu) installation would work, even with the UEFI and Legacy issues?

  
Thank you.

---

### Post by ajgreeny on 2016-11-12
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

You say you have put grub on to a partition which is incorrect; you should have installed it to /dev/sdb, not /dev/sdb2.

If this is a UEFI system rather than legacy BIOS the situation is slightly different as grub does actually go into a partition, but you still must ask for grub to go to the root of the disk, not the root partition, which could be the cause of your confusion; the system sorts out where it actually goes which I believe is the small fat32 EFI partition.

PS:
With Windows in UEFI mode you **must boot the install medium in UEFI mode** and install Ubuntu 16.04 in UEFI as well.
See
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
for lots of info on UEFI and dual booting that way.

---

