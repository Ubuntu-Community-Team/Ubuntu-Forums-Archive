---
title: "Ubuntu 14.04 LTS On Other HDD"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by JMGomes on 2014-12-09
Hello and Good Evening,

1st...

 I had a Computer With 80 GB SATA HDD. So I recently Upgrade to ubuntu 14.4LTS. But Somehow My :mad: PC Going to be Shutdown.

2nd

I bought a New Computer Which is AMD APU, MSI Motherboard where 250 SATA HDD with Windows 8.1 Installed. So now I took the 80 GB SATA HDD From my old PC which Loaded With Ubuntu 14.4 LTS and Installed In my New Computer But When I tried to Make the Ubuntu HDD first piority for boot in BIOS but only shows one USB HDD and Primary Windows HDD. 

But I seleted USB HDD Thought It would be UBUNTU but when I boot it goes to Windows Directly I did Many Changes But Nothing.


" Please Help My Development Environment Is In Ubuntu "

---

### Post by Impavidus on 2014-12-09
I think the new computer uses UEFI. The hard drive from the old one may use MBR partitioning. Those are not compatible. If you change to legacy booting Ubuntu might work (depending on any proprietary drivers you may have installed), but Windows won't work.

---

### Post by JMGomes on 2014-12-09
So it's Means I have to Reinstall My Ubuntu :shock::shock::shock::shock:   whait how to get all my apps update haaa Please any other Solutions.....
 		 			 				:shock:

---

### Post by grahammechanical on 2014-12-09
> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]



[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You could always try Boot Repair. Run it from a live session.

[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

See, What boot Repair recommends.

EDIT: If you are able to load Ubuntu you may find other problems. It is unlikely that Ubuntu will have the video driver for your graphic adapter in this new machine, especially if it is hybrid graphics. Ubuntu will stil be using the video driver for the other machine, espeicailly if it is a proprietary video driver. So, at first boot I would recommend using Advanced Options For Ubuntu and Recovery Mode>Resume to get to a desktop and then using Software and Updates>Additional Drivers tab to install another video driver.

Regards.

---

### Post by oldfred on 2014-12-09
If you have important data, then you have good backups. 
With Ubuntu a new install and restore from your backups is actually pretty easy. 

If you are able to sort out video drivers and other issues you can dual boot with Windows in UEFI mode and Ubuntu in BIOS mode. But not from grub menu as UEFI & BIOS are not compatible.
You have to go into UEFI/BIOS and select boot from it. You may be able to choose from a one time boot key like f12 or f10. But some systems require you to turn on/off UEFI mode or BIOS/CSM/Legacy mode to match install.

---

