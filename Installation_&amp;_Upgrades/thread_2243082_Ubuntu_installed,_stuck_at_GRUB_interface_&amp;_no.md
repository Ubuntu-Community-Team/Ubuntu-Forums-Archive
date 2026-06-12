---
title: "Ubuntu installed, stuck at GRUB interface &amp; no USBs recognized"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by chessKnight042 on 2014-09-06
Hi, I downloaded 14.04 64-bit version of Ubuntu, and loaded it from a usb onto my partitioned SSD, which was running windows 8.1. When I rebooted my computer after installation, the screen went straight to the purple GNU GRUB screen. this screen doesn't display the option for windows boot, which is probably managable to fix. the problem is that it doesnt recognize any usb inputs, which is how i connect my keyboard, mouse, and (i tried) a boot-repair loaded disk. So im currently at a loss for how to send input to my computer at all at this point

As you can probably tell, I'm new to ubuntu so i apologize in advance for any naivete. Salutations and thanks in advance for the help!

---

### Post by grahammechanical on 2014-09-06
Did you follow the advice in this wiki?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note these points.

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.[FONT=inherit][/FONT]
[/LIST]
[LEFT][FONT=inherit]Regards.[/FONT][/LEFT]

---

