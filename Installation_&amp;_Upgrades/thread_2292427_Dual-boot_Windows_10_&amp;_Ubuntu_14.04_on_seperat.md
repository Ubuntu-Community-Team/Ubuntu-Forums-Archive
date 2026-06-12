---
title: "Dual-boot Windows 10 &amp; Ubuntu 14.04 on seperate disk's"
date: 2015-08-27
forum: Installation &amp; Upgrades
---

### Post by daniel245 on 2015-08-27
I have a Windows 10 installation on a 1tb hard disk, I wish to put on my other hard disk (also 1tb) a Ubuntu installation.

What are the prequisits of the installation for dual-boot to work successfully.

Does Windows have to be installed first or Ubuntu? 

How can I get the choice of what OS I want too boot during start-up?

Help would be appreciated!

---

### Post by oldfred on 2015-08-28
Is system newer UEFI or older BIOS?
If newer UEFI hardware, you can install in UEFI or CSM mode, but both systems must be in same mode to easily dual boot. 
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Two drive install can be easier if you disconnect each drive and install system fully on that drive. But still may have to reset/readd entry to UEFI for the disconnected drive.

UEFI is a boot manager which gives a menu of system. Grub is both a boot manager & boot loader. It will show other systems installed in same boot mode, but not if both are not UEFI or both BIOS.

Windows must have its fast startup off which is always on hibernation.

Many details on UEFI and some is general for any install in link below in my signature. 

What specific hardware, brand/model, video card do you have?

---

