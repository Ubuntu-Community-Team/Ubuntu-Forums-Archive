---
title: "Ubuntu 14.04 Install Breaks Bootloader on Samsung NC210 Netbook"
date: 2016-08-24
forum: Installation &amp; Upgrades
---

### Post by john564 on 2016-08-24
Hi everyone, 

I have tried installing the following on my Samsung NC210 netbook:

- Ubuntu 14.04.5
- Ubuntu-Gnome 14.04.5
- Xubuntu 14.04.5

The installation proceed fine, albeit slowly, until it gets to the end, where it just seems to "hang"...

I then powered off the system after it's been in this "hung" state for some time (say, 1 hour+), because it is apparent to me that this is not normal behaviour, and the installer doesn't appear to be doing anything.

I then restart the system and find that the previous bootloader (Grub from a previous Debian Linux installation) has been wiped, and I no longer have a working bootloader, which means that I can no longer boot into Windows 7 Starter which is on another partition of the hard drive.

So, now I am stuck with a completely broken system, which when powered on just brings up a GRUB terminal...

Does anyone know how to fix this?

I'm really not quite sure what to do...

Kind Regards,

John M
Melbourne, Australia

---

### Post by yancek on 2016-08-24
How old/new is this computer?  Post some details on hardware.
Did you try to install these systems on the same partition on which you previously had Debian?  If not can you boot one of the new DVDs to the Desktop and open a terminal and mount the old Debian to see if the expected directories/files are still there?
While booted to the Desktop, open a terminal and run:  sudo fdisk -l (Lower Case Letter L in the command) and post the output here.
You could also go to the site below and download and burn the boot repair software to a CD and boot the computer in question with it.  Make sure to select the option to Create BootInfo Summary and not try any repairs.  Post a link to the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mook765 on 2016-08-24
Welcome to ubuntuforums.
The first step is to gather information about your system. 
To do this please follow the instructions in this link:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
It might be necessary to connect your computer to the Internet via LAN (Ethernet).
Kind regards...

---

