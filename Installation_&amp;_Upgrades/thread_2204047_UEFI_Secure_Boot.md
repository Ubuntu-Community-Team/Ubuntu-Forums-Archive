---
title: "UEFI Secure Boot?"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by junk.here on 2014-02-06
Is there anything I need to do (i.e. tweak BIOS settings) in order to get Ubuntu running on a UEFI Secure Boot laptop?

---

### Post by grahammechanical on 2014-02-06
Since Ubuntu 12.10 Ubuntu has been able to install on machines with secure boot enabled. So, any Ubuntu 64 bit that you download today does not require you to disable secure boot in UEFI. But there may be other things that you need to do and that would also depend on what other operating system that you have on that machine and whether the hard disk is MBR or GPT.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


Regards.

---

