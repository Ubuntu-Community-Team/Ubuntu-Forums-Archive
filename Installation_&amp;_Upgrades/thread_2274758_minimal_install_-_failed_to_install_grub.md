---
title: "minimal install - failed to install grub"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by flaymond on 2015-04-22
Hello, I have a problem here... I cannot install minimal installation because grub bootloader...cannot be installed in dev/sda... the process before bootloader installing part is run smoothly. Using usb to install.

---

### Post by Bucky Ball on 2015-04-22
More detail, please. Dual-boot, UEFI, Ubuntu release?

---

### Post by grahammechanical on 2015-04-22
There is not much information to go on. Is the boot system UEFI with GPT?

The only experience i have with getting a failure to install Grub was when I was experimenting with using the btrfs file system. I needed a certain amount of unallocated space at the front of the disk. I do not have a UEFI motherboard with GPT but I offer you this:

> If the BIOS is setup to boot the disk in [Legacy/mbr mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode"),  installing GRUB2 on a GPT (GUID Partition Table) disk requires a  dedicated BIOS boot partition with a recommended size of at least 1 MiB.  This partition can be created via *[GParted]("https://help.ubuntu.com/community/GParted")* or other partitioning tools, or via the command line. It must be identified with a *bios_grub* flag. The necessary GPT modules are automatically included during installation when GRUB 2 detects a GPT scheme.

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Regards.

---

### Post by flaymond on 2015-04-22
Its bios...I lost my OS again...now I'm hosting iso from my phone...sorry its out of topic...but this is critical for me. Do any of you know any distro below 50mb or 80mb to create liveusb? I sucess to open my pc using backup copy of lubuntu hosted with droidrive...I just can't download anything to pc...since there is no hd memory can be occupied.

---

### Post by flaymond on 2015-04-22
Phew...I got the lubuntu copy as bootable back...after 6 hours struggling with a laptop, a usb, and android phone. Nothing else.

I want to share experience, might help other user that lost his or her os anytime later. So my story start from the beginning of ubuntu minimal installation. I thought ubuntu is bloated, so I wanna try install the minimal one by installing it replacing ubuntu. So the installation process smoothly UNTIL installation prompt to install grub bootloader to master boot record. I hit yes option, but something bad happened after that. Grub failed to install, and my entire hard disk has been erased! I lost my OS just like that. From that time, I try to figuring how to make lubuntu bootable in usb that I use to install minimal iso. So here is my situation, the usb with minimal installation is useless after the failure, I got lubuntu in my android phone sd card, and just one pc (that I lost os). I cannot make new bootable iso, since the OS has been erased. I only got two options, go to computer cafe or 'overlimit' my android. Well at first, I wanna go to computer cafe or cybercafe(whatever you call it), since I know Android is based Linux, there is something android can do in the critical time. I'm googling for the solution, of how to make iso bootable in android. After searching for an hour, aha! I found Droidrive! Installing it, but need to root my phone! Omg! One more burden and challenge, my phone is not supported for towelroot software, nor others that target for most popular phone. So googling for more, and found IRoot/Vroot, I don't know if its safe, since installing it taunting avast the antivirus about suspicious spyware. But it worked like charm. Got my root access immediately by installing it. Then I open Droidrive, trying to figuring how to make it bootable. After reading the manual, its all about hosting the iso without delete any files or space (better than I thought). So I link it to the lubuntu iso, and connect my android to the pc using usb..and boot the pc, select boot from device...and its working...! But I cannot install lubuntu from it, it will conflict my sd card. At least I can try live version, but cannot drag the iso into the hard drive...because its just hosting the iso..:(. Well, I can drag a few small files, but not the 700mb iso. Its too big! Well, thanks to a small usb installer, named mkusb. Download it from ppa, got it installed (57kb), and connect my usb, format it to fat32 and let the mkusb do her job, selecting the iso from the sd card and target to usb. Phew, no need to drag it all over the space. Lubuntu installed and working normally after that. In the end, I found its my mistake, my usb is set to a filesystem type that are not supported for the minimal install(I think its nfts or something like that). Ahh, anyway...I learn a lot today, and using some small distro (dsland a distro that not popular (42 mb with all boot rescue kit like gparted but failed to use them because of the old table kernel). 
Its scary, risky and fun adventure for me, make me more careful after thus. Lesson for today - Do a good research about something you want to do.

Linux is fun!!! :D

*sorry for typos and bad grammars, im writing with my phone righy now.

** Thanks to everybody that trying to helping me out. I appreciate it! :D:D:D

---

### Post by Bucky Ball on 2015-04-22
> **InterProg said:**
> Lesson for today - Do a good research about something you want to do.



+1. I couldn't agree more. Glad you got it sorted.

---

