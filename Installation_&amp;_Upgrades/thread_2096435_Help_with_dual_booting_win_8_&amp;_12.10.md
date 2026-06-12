---
title: "Help with dual booting win 8 &amp; 12.10"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by Sithlyone on 2012-12-19
Hello, I've posted this in the "Newbie" section, however I think the content is more likely to go here better.

I have searched for this but as I am a novice at best, I feel overwhelmed by all of the techie speak.

Basically what I am attempting to do is dual boot ubuntu 12.10 on a new computer that is preloaded with win8.

What I've done so far: I've downloaded 12.10 .iso image and burned it onto a dvd and verified that it is correct. I then attempted to change my bios but am a bit lost here.

I switched from uefi to csm and disabled secure boot. Then I restarted w/ my boot dvd and it did not detect the boot disc. I re-burned another disc and still nothing. I reset my bios back to normal.

Did some more research and found out that my only boot mode is uefi and that I can't change that. Now I have read somewhere that I need to boot Ubuntu in uefi mode.

I attempted to follow the basic instructions on how to dual boot, but sadly I haven't gotten very far. 

If you have any suggestions I would be most appreciative. Thanks for taking the time to help me out.

P.S.- Please be detailed if you can as I most likely am missing something very simple here. Thanks again

---

### Post by offgridguy on 2012-12-19
There may be something that helps in this thread.

[http://ubuntuforums.org/showthread.php?t=2095495]("http://ubuntuforums.org/showthread.php?t=2095495&highlight=UEFI")

---

### Post by oldfred on 2012-12-19
I am not sure I like the thread offgridguy linked to. That user somehow has a full Windows 8 reinstall disk and totally reinstalled both Windows & Ubuntu in BIOS/MBR mode. Not sure he could ever use the recovery partition. But he has converted back to the old way of doing things that most of us know better.

Someone posted that they could not get a DVD to boot in UEFI mode, but only a flash drive. Not sure if just his system or if that is a consistent issue.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
The 64bit version of Ubuntu 12.10 does work and install correctly if you boot in UEFI mode. Some have installed in BIOS mode, but then used Boot-Repair to fix the install as all that has to be done is uninstall the grub2 BIOS grub-pc and install grub-efi. Ubuntu is the same either way with a few minor settings.

Always use Windows MMC to shrink Windows and reboot a couple of times to let Windows run chkdsk or make whatever repairs it likes to make on resizes.

Then you can install Ubuntu into the free space or unallocated space. If you want more than the default of / (root) and swap you have to use manual install. With UEFI grub2's boot loader is automatically installed to the efi partition and you can boot both Windows & Ubuntu from the UEFI menu.

Grub2 has a bug and does not create a correct chain load entry for Windows. But Boot-Repair can also fix that.

grub2's os-prober creates wrong style (BIOS) chain boot entry
 [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Boot-Repair's correct entries
 Windows UEFI loader
Entries from grub (with bug so they do not work)
Windows 8 (loader) (on /dev/sda2)


       
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Sithlyone on 2012-12-20
Wow, thanks for the info. However I don't know that I really understand what a lot of it means. (believe me, I've tried and my head is swimming)

Besides the one on the main ubuntu main site, are there simple step by step instructions? (The ones on the site got me to the point where I insert the dvd and then all hell broke lose)

or at least a step by step of what I need in order to jump back into the basic install?

I'm sorry that I sound like such a newb, but... well I am.

Thank you again for helping me out.

---

### Post by oldfred on 2012-12-20
Do you have a flash drive as that seems to work better. And did you download the 64 bit version, not the 'recommended' 32bit version?

You actually can install Ubuntu  in BIOS/legacy mode if you only have DVD and change setting in UEFI to BIOS and use Boot-Repair to fix the install and convert to UEFI. The real difference is just the grub2 boot loader.

Does DVD boot into live mode so you can test that Ubuntu works? Some have video issues and need settings like nomodeset or others.

Be sure to use Windows mmc to shrink the size of Windows to make space for Ubuntu on your hard drive. Reboot Windows a couple of times as it runs chkdsk and makes repairs to recognize its new size.

If you just want the default of / (root) and swap you can use the auto install, otherwise you have to use manual install or Something else to specify partition size, format (ext4) and use (/ and others). Swap partition has no format.

I do not recommend EasyBCD as it is not needed with UEFI, but otherwise this shows an install.
       Dual-boot Windows 8 and Ubuntu 12.10 on UEFI hardware suggests EasyBCD??
[http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/)

UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard - shows manual partitioning
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

UEFI installs are really the same. The only difference is grub is installed to the efi partition and uses grub-efi. How you boot installer (UEFI or BIOS) is how it installs.
       Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Sithlyone on 2012-12-20
Thanks OldFred. I do have a usb however it didn't recognize that either. I have checked my 2 dvds by putting them into another computer and it recognizes them. However they aren't noticed by my win8 machine.

I haven't partitioned my drive yet in windows so I'll start there I guess.

> You actually can install Ubuntu in BIOS/legacy mode if you only have DVD and change setting in UEFI to BIOS and use Boot-Repair to fix the install and convert to UEFI. The real difference is just the grub2 boot loader.

How do I do this? I believe this is my issue.


Edit: I just attempted to change my uefi in the bios and that is the one option it doesn't allow me to change. Any suggestions?

---

### Post by oldfred on 2012-12-20
I do not know all the different versions of UEFI. But some have a setting that says secure boot, some say enable UEFI boot, others have a setting for BIOS/AHCI boot. And once one is set it make lock the other setting until you change that one back as they are interconnected.

Generally you have to turn fast boot off which is a separate setting. Many have had to turn secure boot off and only then do you get the options to turn on UEFI boot (without secure boot) or with UEFI off, then you may be able to turn on legacy boot.

If still not sure, you can use a camera and post screen shots. Shink to smaller size and upload with the paperclip icon in the edit panel above your message.

---

