---
title: "Lubuntu as default system (no screen for BIOS)"
date: 2021-09-22
forum: Installation &amp; Upgrades
---

### Post by celinemanekis on 2021-09-22
Hi,

Having already several computers running Ubuntu/Lubuntu, I am rather ok with the installation of Lubuntu alongside with Windows. But, today, I am stuck and would love the advice of the community! :P

I am trying to have Lubuntu alongside Windows 8.1 on a laptop with no native screen (broken a few years ago and completely removed), for which I use a VGA screen.
- Laptop is : HP Notebook 650 PC (2017)
- Runs Win 8.1 fine with display on external VGA
- I use my Live USB with Lubuntu 20.04 for the installation (have used it for other installation)

What I have done so far : 
- prepared and shrinked Windows : OK
- used the available space to install Lubuntu. Since it is EFI, it seems that I did not have to create a separate partition for boot)
- installed Lubuntu : everything went smoothly. No errors, it seems installed OK.

My issue is that it always start Windows. 
I have no screen until Windows is started, so : 
[LIST]
[*] I can not see the BIOS 
[*]I can not see if Windows boot manager displays or not 
[/LIST]

What I have done so far : 
- tried to force the BIOS to use my external display (so I could at least view something and work from there!). None of the tricks I came across worked to force the display on the VGA screen.
- ran grub-repair. There was a message mentioning that "Secure boot" was enabled. I forced the update of the BIOS and it seems to have disabled the secure mode.
- ran a second time grub-repair to get the report.

I paste here :
- the info I get from grub-repair : [https://paste.ubuntu.com/p/gy62jJy6nw/](https://paste.ubuntu.com/p/gy62jJy6nw/)
- the boot repair summary after running the recommended repair : [https://paste.ubuntu.com/p/NxxpMW3dX7/](https://paste.ubuntu.com/p/NxxpMW3dX7/)

I am reaching the limit of my knowledge on this topic and would like your help if possible.

What I would wish ideally : being able to choose between Lubuntu and Windows, with Lubuntu as default.

Thank you!

Céline

---

### Post by TheFu on 2021-09-22
> Having already several computers running Ubuntu/Lubuntu, I am rather ok with the installation of Lubuntu alongside with Windows. But, today, I am stuck and would love the advice of the community! 

Advice: Don't post the same question twice minutes apart.

As for the boot order - use an EFI Boot Manager to change the order.  Oldfred is known for posting the relevant tools in the forums. I think **efibootmgr** is one.

If grub is seen, that's far too late in the boot cycle.

---

### Post by grahammechanical on 2021-09-22
This information might be of help. It is old information but it is from the same time period as Windows 8.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note this section:

> **Case when Ubuntu must be installed in UEFI mode**
Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 


[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not.
[/LIST]

If you load Lubuntu 20.04 USB memory stick in UEFI mode, then Lubuntu will install in UEFI mode and the Lubuntu boot loader (Grub) will give an option to load Lubuntu or Windows. But if Windows 8 and Lubuntu are installed in different modes, then you will get a situation like this. I think.

Regards

---

### Post by oldfred on 2021-10-16
You show both Windows & Ubuntu installed in UEFI boot mode to gpt partitioned drive.
But with HP, the use of efibootmgr seems to be limited.
Many with HP update UEFI(may not be required) and then use HP's UEFI settings (not boot menu) to change boot order.

Grub install (or total reinstall) also uses efibootmgr to install grub's UEFI entry & to change boot order to make the ubuntu entry first in boot order. 
Some with HP have said it boots once, but then HP reverts to Windows.

---

