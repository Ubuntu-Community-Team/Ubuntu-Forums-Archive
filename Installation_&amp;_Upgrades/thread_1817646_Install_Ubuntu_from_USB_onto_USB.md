---
title: "Install Ubuntu from USB onto USB"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by farproc on 2011-08-03
I have a PC that has an onboard USB slot.
I have plugged an 8Gb thumbstick into that, and booted the Ubuntu 11.4 server install off of an external thumbstick. There are additionally two SATA drives that are plugged in, but I want to configure later.
 
Everything seems to be working until setup gets to the "Install the GRUB boot loader on a hard disk" step. Which fails.
Ubuntu installer says:
>   Install the GRUB boot loader to the master boot record? <Yes>
  Running "grub-install /dev/sdd"...
  Running "update-grub"...
  Installation step failed
  
I have no choice but to continue with the setup for now, and try and make the usb bootable later. The installer says:

  > You will need to boot manually with the /vmlinuz kernel on partition /dev/sdd1 and root=/dev/sdd1 passed as a kernel argument.

Any clue as to how I get this system to boot?

---
I have booted it once - I think it found a MBR and Grub on one of the internal HDDs - but I need to get it to boot entirely off of the usb drive as I want to remove the SATA disks at some point. 

More worryingly, I tried to 
  sudo apt-get install gparted 
and got this message

> Media change: please insert the disc labeled
 'Ubuntu-Server 11.04 _Natty Narwhal_ - Release i386 (20110426)'
in the drive '/media/cdrom/' and press enter

Each time I press enter is proceeds to download a few packages, then goes back to asking. Holding down enter to install things is not fun :/
Is installation of Ubuntu server onto usb media just not supported?

While I am doing this via an ssh session the login screen on the box itself keeps saying bizarre things like

> [...] sd 7:0:0:0 [sdd] No Caching mode present
[...] sd 7:0:0:0 [sdd] Assuming drive cache: write through


I seem to be in way over my head :(

---

### Post by farproc on 2011-08-03
Problem #1 seems sorted. /dev/sdd is the install usb device, not the boot usb device. /dev/sdc is the boot usb and it seems to be working.

Problem #2 - edited /etc/apt/sources.list and commented out the duplicate "deb cdrom:[Ubuntu-Server..." line from line 5 of the file. After an apt-get update, installs seem fine now.

---

