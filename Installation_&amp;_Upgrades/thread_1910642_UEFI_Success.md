---
title: "UEFI Success?"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by alphaamanitin on 2012-01-17
Has anyone gotten Ubuntu to successfully install on a non-Mac UEFI board?  I have been trying for months, always failing.  First, I couldn't even get it to install, would always fail while trying to install GRUB and quit the installation process.  Now, I can get Ubuntu 11 (I hate unity) to install, but it will not boot, period.  Black screen nothing works.  

Trying to install 64-bit Ubuntu btw.  

Machine:
ASRock Pro3 880G MOBO
16 gb x crucial ram
dual boot- windows from a 128 Gb SSD want to install ubuntu on a 64 gb SSD


AlphaA

---

### Post by oldfred on 2012-01-18
There are some bugs, but some have gotten it to work by partitioning in advance.

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)


Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

---

### Post by lovelyzoo on 2012-01-18
I had much the same problem with 11.10. Note that I did mount and examine the ESP and did not find my failed Windows or successful OSX install removed. Anyway, I've retreated to 10 LTS which I'm now trying to fix up.

---

### Post by alphaamanitin on 2012-01-18
BTW-when I say dual boot it isn't quite what usually comes to mind.  I want to install windows on one drive, ubuntu on the other, and use the UEFI to control boot order of drives.

I'm going to give it another shot soon, but so far, even doing the manual pre-partitioning, I have not gotten Ubuntu to install.

Thanks,

AlphaA

---

### Post by alphaamanitin on 2012-01-26
I see one of my problems.  My system has 16 gb of RAM and grub2 crashes in systems with more than 8gb of RAM.  No wonder the damn thing will never boot!

AlphaA

---

### Post by QIII on 2012-01-26
Unless the UEFI has a problem with it, I can tell you with a great degree of certainty that GRUB2 does not necessarily fail with more than 8GB of memory.  Otherwise, several of my machines would not be useable.

So, I guess the question is:  Does EFI cause that limitation.

---

### Post by alphaamanitin on 2012-01-26
Good to hear.  Sadly, using the newest AM64 build I cannot even boot into the install part of Ubuntu.  I have to manually edit the line to /efi/boot/boot64.efi and hit F10.  Just did that about thirty times, graphic errors every time.  Either RAPIDLY flashing white/back, or a purplish-black/black.  Sometimes at the top if the scree, if I move the mouse around, I can see the mouse.  :(  The drive has ubuntu on it, but it will not boot, at all.  Going to try this:

Boot into a Ubuntu liveCD, create a directory, mount the internal SDD into the directory, chroot into that directory, install grub-efi, update grub, and see what happens. I think I basically just don't understand linux well enough to get it working, and follow the instructions.

Any thoughts?

------------------FINAL UPDATE------------------

I just give up.  Decided to just unplug the windows drive and install Ubuntu in legacy BIOS mode.  Installed, tried to boot, upon booting into Ubuntu 11.10 was greeted with the same graphics error that I experience trying to boot it in UEFI mode.  

Thanks for all the help guys, all the pointers and links, but I think this system just isn't going to work.  I'm going to try old school 10.04 LTS.  

AlphaA

---

### Post by mastablasta on 2012-01-27
> **alphaamanitin said:**
>  
Thanks for all the help guys, all the pointers and links, but I think this system just isn't going to work. I'm going to try old school 10.04 LTS. 

 
why would an older kernel support a new motherboard? you will be missing drivers with it. did you install any proprietary graphics drivers? 
 
and why UEFI would cause problmes as wiki page says linux supports it for quite some time. why would ubuntu then fail at boot?
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
> 

An operating system that can be booted from a (U)EFI is called a (U)EFI-aware OS, defined by (U)EFI specification. Here the term **booted from a (U)EFI** means directly booting the system using a (U)EFI OS loader stored on any storage device. The default location for the OS loader is \EFI\BOOT\boot[architecture name].efi, where the architecture name can be e.g. IA32, X64 or IA64. Some OS vendors may have their own OS loader. They may also change the default boot location.
[LIST]
[*][Linux]("http://en.wikipedia.org/wiki/Linux_kernel") has been able to use EFI at boot time since early 2000,[SIZE=2][*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*][/SIZE] using the [elilo]("http://en.wikipedia.org/wiki/Elilo") EFI boot loader or, more recently, EFI versions of [GRUB]("http://en.wikipedia.org/wiki/GRUB").[[SIZE=2][24][/SIZE]]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#cite_note-debiangrubexample-23")
[/LIST]

---

### Post by oldfred on 2012-01-27
Video issues, not boot loader issue is a common problem. What video card/chip do you have?

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by alphaamanitin on 2012-02-01
Yeah, it looks like now the issue is the graphics card, Asus AMD EAH6850.  Looks like a description of an error you mention in the first link is my prob (black/flashing screen/purple/etc).  

I used alternative disk to install, and it installed (which is only the second time I have got it to install without failing at install grub2-efi), booted up and got the graphical errors.  

@mastablasta, I know linux has been supporting UEFI for quite a while, never the less, until quite recently no matter what I did, I couldn't get grub2efi to install correctly.  Hopefully it is fixed.  

Anyway, thanks for those links Oldfred.  I'll have to give it another go soon.  

AlphaA

---

