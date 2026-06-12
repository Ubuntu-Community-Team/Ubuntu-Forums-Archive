---
title: "[HELP NEEDED] Problems dual booting Ubuntu."
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by Shawn.Ds on 2015-11-28
Hello,
I want to dual boot with Ubuntu,But i am having problems,to be specific,i have 2 seperate but related problems
1) whenever i try to install ubuntu i get the following error>  [COLOR=#111111][FONT=Ubuntu]force UEFI installation?...this machine's firm ware has started the installer in UEFI mode but it looks like there may exist operating systems already installed using "BIOS compatibility mode"...If you wish to install in UEFI mode and dont care about keeping the ability to boot one of the existing system,you have the option to force that here instead of  "Install alongside Windows"  i tried installing ubuntu anyway but was unable to boot into windows.3 hours of struggling later,i deleted ubuntu and grub and got windows back


2) while booting from USB,i get a black screen(no signal) using the "try ubuntu" option,i realised this was because of my card NVIDIA GTX 970 using propreitary drivers,so i used the 'nomodeset' command to successfully boot into Live Ubuntu.
Here lies the issue,There are 2 ways from which the computer boots from the same USB,It shows up as 2 USB drives in my boot menu  UEFI * USB drive* and just *usb drive* , by default,the PC boots into the UEFI *USB Drive* , this is the one where the options are shown i.e try ubuntu,install ubuntu etc.The *USB Driver* however doesn't give these options(so i cant edit the 'nomodeset' command in) and directly goes into a black screen/no signal.

I feel if i boot from *USB Drive* instead of UEFI *USB Drive* it should detect my Windows 8.1 and allow me to install ubuntu alongside it,But it doesnt allow me to see the desktop because i cant add the 'nomodeset' command


Any help will be appreciated[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-11-28
You should read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **Boot mode matching** -- If you're dual-booting with  another OS, the two OSes' boot modes should match. Most computers that  ship with Windows 8 and later use UEFI to boot that OS, so this  configuration dictates use of UEFI mode when installing and booting  Ubuntu.

It seems that you have a version of Windows (which one by the way?) that has been installed in BIOS compatibility mode. Also called legacy mode. And you ran the Ubuntu Live session in EFI mode and so Ubuntu gets installed in EFI. And the result is that the Ubuntu boot loader (Grub) will no be able to load Windows.

It seems that Windows 7 is usually installed in BIOS mode even on motherboards that had UEFI boot systems. That is not a problem unless we install Ubuntu in EFI mode. Which is possible with a UEFI boot system motherboard. That is the source of your first problem.

I think that both problems will disappear if you boot the Ubuntu live session using the *usb drive* option and let the live session run. Once the live session loads it should give you a TRY - INSTALL option. OR,

At the first purple screen with the two icons of a human and a keyboard press Enter. Select the language and at the underlying page press F6 to enter nomodeset.

Regards.

---

