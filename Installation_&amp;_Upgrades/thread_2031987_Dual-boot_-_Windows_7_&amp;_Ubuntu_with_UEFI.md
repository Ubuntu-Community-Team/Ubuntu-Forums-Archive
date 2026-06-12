---
title: "Dual-boot - Windows 7 &amp; Ubuntu with UEFI"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2012-07-22
Hey everybody! :) 

I've managed to persuade my friend to give Ubuntu a try. He's running Windows 7 on his system. I'm going to tell him to sign up on the Ubuntu Forums, but I'd also like to be able to provide support, if he runs into any problems while attempting to dual-boot. I've suggested that he burn an Ubuntu LiveCD and test it out on his system before going for the installation. Now, what I would like to know is if there are any differences in dual-booting when a system has UEFI? His motherboard has UEFI. To my understanding, UEFI is supposed to be a replacement for BIOS? I'd basically like to know how to dual-boot Ubuntu with Windows 7 on a system with UEFI. Any help is appreciated!

---

### Post by UltimateCat on 2012-07-22
I know that you need information for UEFI and Ubuntu but I was only able to find info. for Windows 8 and Fedora.
Perhaps this will help you.  Trying to help-

[http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187](http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187)

[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

This website is about UEFI and Ubuntu ( this might be the help you need)
[http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270](http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270)

I'm dual booted with Windows XP and have Ubuntu 10.04...but I have an MSI motherboard.  I've never had any problems with a dual boot.

Best Regards

---

### Post by derekpock on 2012-07-22
Basically you just need to have the Ubuntu disk to boot first before the hard drive and everything else should fall into place. No other configuration with or without a certain BIOS is needed.:popcorn:

---

### Post by Shadius on 2012-07-22
> **UltimateCat said:**
> I know that you need information for UEFI and Ubuntu but I was only able to find info. for Windows 8 and Fedora.
Perhaps this will help you.  Trying to help-

[http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187](http://www.zdnet.com/blog/open-source/linus-torvalds-on-windows-8-uefi-and-fedora/11187)

[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

This website is about UEFI and Ubuntu ( this might be the help you need)
[http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270](http://www.zdnet.com/blog/open-source/shuttleworth-on-ubuntu-linux-fedora-and-the-uefi-problem/11270)

I'm dual booted with Windows XP and have Ubuntu 10.04...but I have an MSI motherboard.  I've never had any problems with a dual boot.

Best Regards

Thank you. Will check these out.

---

### Post by Shadius on 2012-07-22
> **derekpock said:**
> Basically you just need to have the Ubuntu disk to boot first before the hard drive and everything else should fall into place. No other configuration with or without a certain BIOS is needed.:popcorn:

So there's no difference in installing Ubuntu on a system with UEFI? It's the same as creating the necessary partitions? I was under the impression that there had to be an EFI partition or something like that.

---

### Post by derekpock on 2012-07-22
> **Shadius said:**
> So there's no difference in installing Ubuntu on a system with UEFI? It's the same as creating the necessary partitions? I was under the impression that there had to be an EFI partition or something like that.

Not really no. Ubuntu, if you are using the Live CD, will go though the basic steps of partitioning drives during installation.

---

### Post by Shadius on 2012-07-22
> **derekpock said:**
> Not really no. Ubuntu, if you are using the Live CD, will go though the basic steps of partitioning drives during installation.

Okay, thank you. That's basically what I needed to know. So I won't encounter anything out of the ordinary from what I usually see when installing Ubuntu. Much appreciated.

---

### Post by derekpock on 2012-07-22
> **Shadius said:**
> Okay, thank you. That's basically what I needed to know. So I won't encounter anything out of the ordinary from what I usually see when installing Ubuntu. Much appreciated.

Basically no you shouldn't. Ubuntu is advanced enough to detect such hardware and is able to cope with it. Be sure to have an internet connection when installing, Ubuntu might need to install a driver for restricted hardware first before installing.

---

### Post by Shadius on 2012-07-22
> **derekpock said:**
> Basically no you shouldn't. Ubuntu is advanced enough to detect such hardware and is able to cope with it. Be sure to have an internet connection when installing, Ubuntu might need to install a driver for restricted hardware first before installing.

Oh yes, I forgot about the graphics card. Will do.

---

### Post by mastablasta on 2012-07-23
> **Shadius said:**
> So there's no difference in installing Ubuntu on a system with UEFI? It's the same as creating the necessary partitions? I was under the impression that there had to be an EFI partition or something like that.
 
> **derekpock said:**
> Not really no. Ubuntu, if you are using the Live CD, will go though the basic steps of partitioning drives during installation.
 
 
there actually is a difference: [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by vasa1 on 2012-07-23
I'll be watching this thread with great interest. I wish there's a way to add UEFI to the title since that's the main thing.

My suspicion is that it is not going to be straightforward. I hope I'm wrong.

Anyway, all the best.

---

### Post by nothingspecial on 2012-07-23
Added UEFI to thread title.

---

### Post by Shadius on 2012-07-23
> **nothingspecial said:**
> Added UEFI to thread title.

That was fast! Thank you!!

---

### Post by oldfred on 2012-07-23
There is a lot of difference and many are confused. There also was a bug (one of many) with UEFI and grub that it erased the efi partition, so best to backup the efi partition before installing. Depends on version as supposed fixed in newest.

UEFI bugs:
UEFI computer in BIOS mode, installer installs grub-efi - New July 2012
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616)
[http://ubuntuforums.org/showthread.php?t=2028699](http://ubuntuforums.org/showthread.php?t=2028699)

Deletes Windows efi partition Fixed March 2012 partman-efi (24ubuntu3) 
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16 Fixed March 2012
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Some threads:
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

---

### Post by nehaljwani on 2012-10-08
You don't necessarily need to dual boot Windows and Linux on UEFI. Follow the guide [http://www.youtube.com/watch?v=PEou2dIcMSE](http://www.youtube.com/watch?v=PEou2dIcMSE) to convert your UEFI to MBR-BIOS without loss of data. Or read about it here: [http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html](http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html)

---

### Post by Mohamed Badawi on 2013-03-15
In fact, I have been using Ubuntu since 2005. I had no problems in dual-booting it with windows Vista or Windows 7, whether 32-bit or 64-bit. But when I tried to dual-boot them on my new laptop (Dell Inspiron 15R 5520 core i5) I am stucked with the issue of "UEFI". All my attempts went in vein up till now. I heard Ubuntu is working on solving this problem. I hope it is solved soon!

---

