---
title: "I need help with UEFI installation"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by kernco on 2013-02-11
I'm trying to install Ubuntu 12.10 on my MacBook Pro (8,2). I installed it successfully a few weeks ago, but then discovered I did it using BIOS boot, which is how I've always done it, and that makes it so that my laptop will always use the discrete ATI graphics card and never the Intel integrated graphics. I noticed while using the laptop in Ubuntu that battery life was much worse than in Mac OS X, and the case seemed to be warmer than normal.

So I'm trying to reinstall to boot using UEFI. This ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) seems to be the most "official" guide to doing it, but I've run into a few questions this doesn't answer. Since I want to dual-boot OS X, I have to do the manual partition option. The problem is that I have to create an EFI partition that is at the start of the disk, but one is already there. I assume that's what Mac OS X uses. Should I select that partition (/dev/hda1) to install the boot loader? Will it erase whatever OS X boot information is there?

To try to answer this question myself, I did some googling and came across other instructions which say I should choose the MBR (/dev/hda) to install the bootloader. Will that know to do EFI and not BIOS? Will it keep OS X bootable?

---

### Post by oldfred on 2013-02-11
I do not know about Macs. But some links to info that may be useful.

       Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Caution on UEFI boot Mac
[http://ubuntuforums.org/showthread.php?t=2012588](http://ubuntuforums.org/showthread.php?t=2012588)

---

### Post by kernco on 2013-02-11
> **oldfred said:**
> 
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)


This is actually the one I came across while googling that says to choose /dev/hda not /dev/hda1 to install the boot loader. Most of the other links you provided and other things I've read seem to indicate that doing that would be a very bad idea. I'm still not sure if I can safely install the boot loader to /dev/hda1 without messing up the ability to boot into OS X.

---

### Post by oldfred on 2013-02-12
BIOS boot loaders are in sda or hda. But I do not know how some of the other boot loaders work and you may be chain loading back into the MBR just to find boot code?

UEFI boot loaders are in the efi partition which is usually the first or sda1. Some PC's have efi partition as sda2 or even sda3 but usually just after a Windows recovery partition which is not large.

You may want to search for threads with comments by   trogdor1138 as he is the only one that says he used efi to boot Ubuntu on a Mac. Everyone else uses something else.

---

