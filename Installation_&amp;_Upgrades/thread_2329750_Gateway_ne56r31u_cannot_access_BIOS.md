---
title: "Gateway ne56r31u cannot access BIOS"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by mjmiracle on 2016-07-04
I have previously installed Ubunutu 14.04 on this gatweay laptop. however, due to a career change I now need to have windows on this laptop. I have a bootable usb drive with windows 7 on it ready to go. the problem arises when I try to access the bios to select my boot order. I CANT GET TO THE BIOS!!!! After a little google searching turns out this seems to be a common issue. I have not been able to get any of the solutions i have seen so far to work. Have even tried to boot the usb drive from the command line in GRUB. I am at my wits end. This is my first post in the forums. Take it easy on me....I'm a total noob:).
Any help will be much appreciated.

I have tried using all the functions keys (tapping and holding). I have also tested to make sure that the hdd is booted in legacy mode and that my current OS was installed in legacy mode..... im not a fan of UEFI. it confuses me apparently.

---

### Post by mjmiracle on 2016-07-04
Nevermind. I am a complete moron. Just realized my function keys aren't dedicated, you have to hold function then hit them...used an external keyboard with no secondary functions to the "f" keys and now it is smooth sailing. I apologize for wasting your time.:oops:

---

### Post by grahammechanical on 2016-07-04
I know how to enter the BIOS on my machine. I do not know how to enter the BIOS on any other machine. What does the user guide say you should do? My machine gives me a screen that tells me what key to press to enter the BIOS. I tap that key slowly from the moment the manufacturer's splash screen appears. And then I am in the BIOS settings utility.

This is not caused by the installation of Ubuntu. When we switch on a computer the motherboard runs a series of Power On Startup Tests (POST). Then motherboard sets itself according to the settings in the BIOS. Until that happens the motherboard does not even know it has a hard drive connected or what type of drive its. Finally, it follows the settings in the BIOS to access a drive to look for a computer OS. It is then that it finds the boot loader (grub) and Grub starts to do it stuff.

So you see, once Grub starts to load to opportunity the enter the BIOS has past. Ubuntu and it boot loader has no ability to prevent the user from entering the BIOS/UEFI settings utility.

You should access the motherboard user guide. The Gateway web site may have a PDF version you can download.

Regards.

---

