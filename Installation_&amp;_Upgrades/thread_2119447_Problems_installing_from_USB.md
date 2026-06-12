---
title: "Problems installing from USB"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by Nuglord on 2013-02-23
Hi, wanted to start off by letting you know I'm a total newbie to Ubuntu and Linux in general, and additionally apologize if this topic is a duplicate as I am having a hard time understanding some of the more technical language on this forum.

Basically I'm having problems installing Ubuntu from USB. I'm attempting to install Ubuntu via a 2GB USB Drive on a Toshiba Satellite C855D-S5340. I get the UEFI GRUB GUI screen with normal options, but upon selecting any of the options the screen goes black, and the drive disconnects, and the laptop keyboard seems to lose connection as well. It remains this way until restarted.

 I've disabled Secureboot as described in this guide:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I attempted to locate the Quickboot/Fastboot and Intel SRT options, but was unable to locate anything similar. 

I've also tried several different versions of Ubuntu including 64-bit versions of the 12.10, 12.04, and 12.10 secure remix. 

I'm really not sure what additional information to provide. I'd very much appreciate any assistance. I picked this laptop up on sale for really cheap and am trying to swap it to a Linux exclusive machine for taking notes on a quick and easy platform. Once again I apologize if this thread is a duplicate or misplaced, and let me know if additional information is required.

Also here are some basic specs:
Processor* AMD Dual-Core E1-1200 Accelerated Processor
Graphics Engine* AMD Radeon&#8482; HD 7310
Memory* 4GB DDR3 1066MHz memory

---

### Post by debodas on 2013-02-24
Hi there Nuglord.

A couple of questions about your problem:
What OS is this computer currently running? Also. what program did you use to make a bootable USB?

If you get the grub screen, does this mean you have already installed linux? Or do you mean the BIOS instead of grub?

---

### Post by Nuglord on 2013-02-24
> **kingnick42 said:**
> Hi there Nuglord.

A couple of questions about your problem:
What OS is this computer currently running? Also. what program did you use to make a bootable USB?

If you get the grub screen, does this mean you have already installed linux? Or do you mean the BIOS instead of grub?
It's Windows 8. I went through the BIOS again, and was able to boot Ubuntu installer using the Universal USB Installer, using version 12.10 by booting disc in non-UEFI mode. However, I've went through the installer twice, and am now stuck again.

The Ubuntu v. 12.10 installer goes all the way through, and asks for a reboot. I've tried leaving the USB media in, which results in it asking to install again, or taking it out, which results in a black screen with a hyphen at the upper right corner of the screen with no response from any input. At this point I'm not sure exactly what to do.

---

### Post by debodas on 2013-02-24
Ok, when it reboots, are you selecting restart, or shutdown? If you are selecting restart, select shut down instead. Keep the USB stick in when shutting down. Take the USB stick out, and restart, booting into the BIOS. Change the boot order in the BIOS so that the HDD is the primary boot option.
Does this work?

Edit - Please check out [http://ubuntuforums.org/showthread.php?t=2088425](http://ubuntuforums.org/showthread.php?t=2088425) for good information about dual booting Windows 8 and Ubuntu.

---

