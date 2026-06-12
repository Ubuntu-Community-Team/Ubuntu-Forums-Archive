---
title: "EFI Installation CD (i386 / AMD64) need"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by cabdouch on 2007-12-03
The normal i386 Install CD uses an El Torito partition with an executable to kick off the install process. 
This boot process is considered a "Legacy" boot and expects that the BIOS is a traditional Legacy BIOS. 
i.e. The BIOS will load the file into memory at 0:7C00 and execute it there with the standard Interrupt Vector table at 0:0, BIOS Data area at 40:0, interrupt handlers such as Int 13h, Int 16h, etc. 

I have an EFI Only BIOS which has no CSM (Compatibility Support Module) yet. An even when we do get the CSM added, since Linux supports an EFI only BIOS based platform, it should have an Installation CD to match. One which presents a directory of files to the EFI Boot Manager, including Startup.nsh, elilo.efi, elilo.conf, initrd , and vmlinuz. 

Here is how I do Installs at the moment. 

1. I insert the Debian i386 Net-Inst CD into a system with a running OS. I also install a USB Key. 
2. I copy the files initrd and vmlinuz from the "install.386" directory on the CD to the USB Key. 
3. I found the latest version of elilo.efi somewhere in the past and keep a copy of it. I copy it to the USB Key. 
4. Now I move the CD and USB Key to the EFI based system I want to install Linux on and boot to EFI Shell. 
5. The USB Key gets a File System (fs0:) since it has a Fat file system on it. I change to this file system using the command "fs0:" and return. 
6. I execute the install with the following command: 
elilo -i initrd vmlinux ro root=/dev/ram0 

This will kick off the install and look for the CD in the CD Drive. Linux will properly detect a EFI Base system and create a EFI Partition during the partition program, though I usually run this manually to make the partitions exactly how I like them. 

Linux is supposed to load the efivars module which allows it to create a Boot Entry in the EFI Boot Manager for the Linux install, copy the files initrd.img and vmlinux to this partition (usually in the Debian subdirectory), and copy elilo.efi and elilo.conf to the EFI partition. 

But in my case, I am having a problem with my BIOS working with efivars (another bug report). 

The point of this posting is, that there should be an EFI Install ISO which has this expanded El Torito partition (FAT File System instead of just a boot image). 

I am going to work on creating one and see about how to get it back to the standard distro channels. 

If anyone else has had this problem, or wants to help, or knows if this has been done, then post please. 

Thanks.

---

