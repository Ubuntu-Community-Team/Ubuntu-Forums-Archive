---
title: "Installation on a MacBookPro with no optical drive: advice needed on bootloaders, etc"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by neuromorphic on 2011-03-21
Hi,

I am about to install Ubuntu onto my MacBook Pro (5,2).  However the hardware configuration is a little unusual, and may cause complications.  I have removed the optical drive, and replaced it with a SSD, onto which I wish to install Ubuntu.  Since this will be the second internal HD, whatever bootloader I'm using will need to be able to see this second disk, and perhaps the MBP hardware may have trouble with this (I don't know)?

My questions are the following:

1) What bootloader should I use?  (I'm not sure what exactly are the distinctions between rEFIt, grub2, grub2-efi, etc.)

2) Which partition[s] should I install this bootloader on?  I am confused about whether I will need to install grub2 (or grub2-efi?) on the MBR of 'sda' (the HDD), or perhaps on the 'EFI partition' on that disk (originally created by OSX?), or perhaps somewhere else, or even at multiple locations.

3) How do I perform this installation?  A link to the right (up-to-date) guide would be appreciated.  (I've been browsing through perhaps rather too many help pages and forums, all written at different points in time over the last few years, when the technologies (GRUB2, distros, etc) were at different levels of advancement.  And in that time, people have made progress in getting various things working on MBPs, their methods will have changed, and so will their advice/recommendations.)  One thing in particular that I'll need to know is what to do when running the Ubuntu installer, to direct it to put the bootloader in the right place (or maybe we won't want the installing of the bootloader[s] to be handled by the Ubuntu installer).  Also, it's still unclear to me what things like 'GPT-sync' (or 'bless') do, and what role they might have to play in this.

4) How do I accomplish this without having an internal optical drive?  In the past I've been unable to boot MBPs from a Linux USB drive, and I understand that there are particular MBP issues with this.  FWIW, the main HDD has already been partitioned into OSX and Windows (which I don't care about being able to use, actually, so if a proposed method makes Windows unusable it's of no consequence really).  As such, perhaps some installation (eg of bootloaders) can be performed from within OSX?  Alternatively, I do have USB sticks and a USB external optical drive that I can use.  I also have access to another computer that's running Debian, so I thus have access to any Ubuntu/GNU software tools that may be needed.  Finally, I can even put the optical drive back into the MBP temporarily if necessary in order to accomplish this installation.

I've been looking at a number of webpages and forum pages on this and related topics for a several weeks now, but I feel I'm now getting a bit lost in it all, and now I think I'm actually starting to become more confused the more I read.  So, I'd appreciate a bit of expert advice at this stage.  Thanks.

---

### Post by srs5694 on 2011-03-21
I can't answer all of your questions, but I can provide answers to some of them, and suggestions/pointers for some of the rest....

> **neuromorphic said:**
> I am about to install Ubuntu onto my MacBook Pro (5,2).  However the hardware configuration is a little unusual, and may cause complications.  I have removed the optical drive, and replaced it with a SSD, onto which I wish to install Ubuntu.
...
1) What bootloader should I use?  (I'm not sure what exactly are the distinctions between rEFIt, grub2, grub2-efi, etc.)

GRUB is a boot loader that can directly boot Linux and various other OSes, including OS X (but with some limitations for OS X). It comes in two major versions, GRUB Legacy and GRUB 2. Ubuntu uses GRUB 2. GRUB 2 comes in two varieties, known in Ubuntu as grub-pc and grub-efi. The grub-pc version is intended for BIOS-based computers; it installs key parts of itself in the boot code area of the Master Boot Record (MBR) and relies on the BIOS to read and execute the boot code. The grub-efi version is intended for systems based on EFI; it installs key parts of itself in the EFI System Partition (ESP), where the EFI reads the files to launch GRUB. Through version 10.10, Ubuntu installs grub-pc by default. Although Macs are EFI-based, this usually works, since Macs include a BIOS compatibility mode to help them boot Windows, and this mode can also launch grub-pc. This approach has drawbacks, though. Personally, if Windows isn't to be installed, I prefer using grub-efi and launching Linux in EFI mode, although this also has drawbacks. More on all of this shortly....

The rEFIt boot loader is EFI-specific. It presents a set of GUI icons that can be used to select the boot OS -- either the EFI-type boot loaders as installed by grub-efi or MBR options such as presented by grub-pc. It's possible to dual-boot a Mac without rEFIt, but it's easier to do so with rEFIt, whether you use grub-pc or grub-efi. When you do so, you'll select between OS X and Linux using rEFIt and then use GRUB to select which Linux kernel to boot (and perhaps have a second option to boot OS X). rEFIt can't boot Linux directly; it relies on GRUB (or theoretically some other Linux-capable boot loader) to finish the job of booting Linux.

> 2) Which partition[s] should I install this bootloader on?  I am confused about whether I will need to install grub2 (or grub2-efi?) on the MBR of 'sda' (the HDD), or perhaps on the 'EFI partition' on that disk (originally created by OSX?), or perhaps somewhere else, or even at multiple locations.

This depends in part on whether you use grub-pc or grub-efi. I've seen recommendations to install grub-pc to either the MBR or the Linux boot partition. It should *not* be installed to the ESP. If you use grub2-efi, at least part of it will have to be installed to the ESP, but the Ubuntu installer can't do this automatically. [I've written a Web page](http://nessus.rodsbooks.com/ubuntu-efi/index.html) about booting Macs in EFI mode that provides some of the details of how I got this working myself; however, some of the details are likely to differ between Mac models.

Incidentally, the ESP is a standard part of any bootable EFI-based computer. It holds drivers for the EFI and boot loader components. OS X creates the ESP automatically whenever it partitions a disk.

> 3) How do I perform this installation?  A link to the right (up-to-date) guide would be appreciated.  (I've been browsing through perhaps rather too many help pages and forums, all written at different points in time over the last few years, when the technologies (GRUB2, distros, etc) were at different levels of advancement.

See my previous link for my own solution; but be aware that running Ubuntu on Macs is somewhat "bleeding-edge;" most Ubuntu development is done for standard PCs, and Macs differ surprisingly much between models, so there are a lot of model-specific "gotchas" -- and these vary from one version of Ubuntu to another! What's more, although Macs are EFI-based, Apple's version of EFI differs from other versions of EFI, some of which are starting to appear on PCs. All of this complicates proper Mac support in Ubuntu (or any other non-Apple OS).

FWIW, the 11.04 release of Ubuntu, due out in about a month, is likely to be much better for native EFI-mode installations than is the current version. You might want to consider waiting a month just to use that version, or maybe even install the alpha (or beta, if it's available) version now and upgrade when the final version comes out.

> Also, it's still unclear to me what things like 'GPT-sync' (or 'bless') do, and what role they might have to play in this.

The gptsync utility creates a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) which is the ugly and dangerous hack that Apple (IMHO foolishly) chose to use as part of its solution to enable Windows to install on Macs. A hybrid MBR is a violation of the standard for the GUID Partition Table (GPT) used by Macs. In a hybrid MBR, up to three GPT partitions can be added to the protective MBR, which is a standard part of GPT that's designed to keep GPT-unaware utilities from damaging the disk. The end result is that Windows can boot from one of the three hybrid MBR partitions and OS X can use all the GPT partitions. The problem is in keeping this all synchronized; it's far too easy for the MBR and GPT partitions to get out of sync when you make changes, thus causing untold problems.

Linux is fully GPT-aware and so does not need a hybrid MBR. Unfortunately, the BIOS compatibility mode in Apple's EFI uses a hybrid MBR (or a non-GPT MBR partition table) as a trigger, so it is, AFAIK, impossible to boot a Mac using BIOS compatibility mode without a hybrid MBR (or perhaps a USB flash drive or something with an MBR plugged into the computer). This is my primary reason for saying that EFI booting Linux on a Mac is desirable; you can do away with the dangerous hybrid MBR.

> 4) How do I accomplish this without having an internal optical drive?  In the past I've been unable to boot MBPs from a Linux USB drive, and I understand that there are particular MBP issues with this.

I've not been following this issue closely, but there have been discussions here about booting Macs using USB flash drives, so you may want to search the forums for such discussions.

> FWIW, the main HDD has already been partitioned into OSX and Windows (which I don't care about being able to use, actually, so if a proposed method makes Windows unusable it's of no consequence really).

In that case you've already got a hybrid MBR, and you must be *very very careful* in how you repartition the drive. My recommendation is to download [GPT fdisk (gdisk)](http://nessus.rodsbooks.com/ubuntu-efi/index.html) for OS X and use it to create a fresh (non-hybrid) protective MBR:


[list=1]
[*]Launch the program on the disk by typing "sudo gdisk /dev/disk0"
[*]Type "x" to enter the experts' menu
[*]Type "o" to view the MBR partitions and verify that they're in hybrid mode
[*]Type "n" to generate a new hybrid MBR
[*]Type "o" again to verify that it's correct
[*]Type "w" to save your changes.
[/list]


You can then proceed to repartition and install Linux. If you decide to keep Windows, you'll then need to generate a new hybrid MBR to keep it happy.

> Finally, I can even put the optical drive back into the MBP temporarily if necessary in order to accomplish this installation.

That might be necessary. Another option might be to buy an external DVD drive, but I don't know if Macs permit booting from such devices. (If it uses eSATA, I'd think it'd be more likely to work than if it uses USB.)

---

