---
title: "Msi ge 60"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by antoine.conde on 2013-12-14
Hello everyone,

I'm french so sorry for my english

I just post on the forum because I have a problem with installing Ubuntu 13.10 64bit .

I  download the 64bit 13.10 version of Ubuntu and I get to the home screen  that offers me several choices ( Try Ubuntu , install , etc ...) but  when i select " Try Ubuntu" or "Install Ubuntu" i have a black screen appears so I have to restart my pc. After several attempts to change the bios I tried to install Ubuntu 13.10 32bit and its working! ( I am writing this post from Ubuntu ) .

I 'm not dual boot , there just Ubuntu on my pc .

I have a MSI GE 60 2oth with this config: [http://fr.msi.com/product/nb/GE60-2OE.h](http://fr.msi.com/product/nb/GE60-2OE.h) ... cification

So I just ask you a help to install the 64bit version of Ubuntu because I have 8gb of ram and 32bit take care of that 4 GB max.

Thank you in advance to those who help me because I really need it.

Regards,

SupAntoine .

---

### Post by bapoumba on 2013-12-14
Hello, I get a 404 on your link, it must have broken when you copy/pasted it.

What kind of video card do you have ? I might not be able to help you but others will.

---

### Post by grahammechanical on 2013-12-14
There is something that you can try. Run the 64bit live session and

1) At the first purple screen press Enter
2) At the language screen select the language and press Enter
3) At the Try Ubuntu - Install Ubuntu Screen press F6
4) At the bottom right of the screen a drop down menu will appear, select nomodeset and press enter.
5) Press Esc to get back to the Try Ubuntu - Install Ubuntu screen and select Try Ubuntu and press enter.

We can set a combination of those F6 options and with some machines we need to try a combination of options in order to get a working live session from which we can install.

Regards.

---

### Post by oldfred on 2013-12-14
The 32 bit only installs in BIOS mode.
The 64 bit will offer from a  UEFI/BIOS menu both UEFI boot with grub menu and the purple BIOS boot screen.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Your English is fine, but there is also a French forum.

 French Forums
 [www.ubuntu-fr.org](www.ubuntu-fr.org)

---

### Post by antoine.conde on 2013-12-14
My specification : [http://msi.com/product/nb/GE60-2OE.html#specification](http://msi.com/product/nb/GE60-2OE.html#specification)

Thanks for try help me ! =)

---

### Post by efflandt on 2013-12-16
I have a GE60-20E. I specifically got an earlier model with Win7 on 1 TB hard drive, so I did not need to figure out UEFI. I used **nomodeset** after I got that black screen the first time I tried booting 64-bit 13.10 iso and that worked. I do not know if it was really needed or if I just did not wait long enough when screen went black during hardware detection, but I thought it might be needed with the dual Intel/Nvidia graphics (sometimes nomodeset is required for nvidia alone).

After you install nvidia drivers, to use nvidia graphics put **optirun** before the command. Although some other things need to be done to run Steam Source games.

---

