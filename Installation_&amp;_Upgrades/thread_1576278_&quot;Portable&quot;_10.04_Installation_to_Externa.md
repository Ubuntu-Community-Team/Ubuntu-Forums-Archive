---
title: "&quot;Portable&quot; 10.04 Installation to External Harddisk"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by JasonInferno on 2010-09-17
I've got an Asus notebook, a 230GB external harddisk, and an installation CD for Ubuntu 10.04 LTS. What I want to do is do a full install of 10.04 to my harddisk and have it boot on any USB-bootable computer. I'm aware that I need to change BIOS settings and allow the computer to boot from the USB device first.
I'm not a newbie to Linux in any way. I've been a steady user since 8.10, and the jargon and geek-lingo is something I can understand - one thing that sets me apart from the other support requesters!
 
My sketchy solution is to run the LiveCD from a host computer, set up Ubuntu as per usual, ***but*** install it to an (unmounted) external harddisk and install GRUB to that same disk.
 
Now, before I commit to anything, I want to make sure:
[LIST]
[*]I can boot up 10.04 on any USB-bootable machine with no direct MBR modifications on the host computer,
[*]The host PC that I used to install Ubuntu to the external HD can boot from it's primary OS (Windows 7 Home Premium 32bit) and not encounter any bootloaders, like GRUB,
[*]The host PC doesn't have anything installed on it, i.e. bootloaders. This is meant to be taken around with me, not used on one specific machine.
[*]The external HDD can be reformatted to FAT for general file storage use, and not be corrupted,
[*]No host computers have any modifications done to them while running Ubuntu (i.e. partition corruption on the local machine, failure toboot in the future),
[*]I have a proper installation (or as far as a full install to a USB HDD can go), not a WUBI, compressed squashfs, UNetBootin, or live installation.
[*]That the USB HDD is "plug-n-play" bootable, i.e. I can hook it up, boot up, set to boot from USB, and have it boot cleanly - no bootloader command lines.
[/LIST]If this is possible, please get back to me. I'm not too picky on other specifications like if it can be updated or not.
If something can't be done as I specified, please give me a fix or alternate option. I don't want any machines to get wrecked in the process.
 
Also, by "portable", I mean having a proper install to an external HDD, not a live or USB flash drive install.
 
Also, sorry if I seem to picky. I'm easy for any changes in my sketchy plan.

---

### Post by Fafler on 2010-09-17
Thats all possible. Just go for it! Although you might want to remove the internal harddrive during installation, just to be 100% sure it won't touch existing data.

---

### Post by sikander3786 on 2010-09-17
You can boot your hard disk on any computer without making changes to the MBR of the host computer.

The host will continue to boot its default operating system, the only differnce will be the bios pointing to either the IDE/SATA or USB HDD.

Nothing will be/needs to be installed on the host computer.

The remaining space in the external HDD can be reformated to whatever format you like. You'll need to create a new partition in the remaining space. Corruption, well that depends. No worries but no guarantees either.

Host computer might not get any corruption until you know what you are doing. If you mount the host partitions in Ubuntu and delete/overwrite some system files, thats all you need.

*I will skip your question regarding the proper install. Don't know if this type of installation will slow down on some other PCs/hardware, will either work or not.*

USB HDD will be plug n play and most probably you won't need to type in any commands until something gets messed up.

---

### Post by JasonInferno on 2010-09-18
Thanks for your assurance guys.
I'm not going to attempt removing any of the internals druves, though. It's a family computer, and I haven't got any time or place to take it and unhook the drives - also take into consideration I'm not a big hardware buff, so I don't wantto screw anything.
 
But the assurance is all I need. I might see if I can get some cheap host computer or a friend's old box to host the installation.

---

