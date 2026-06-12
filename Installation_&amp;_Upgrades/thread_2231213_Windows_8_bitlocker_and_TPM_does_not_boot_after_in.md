---
title: "Windows 8 bitlocker and TPM does not boot after installation of Ubuntu 14.04 non efi"
date: 2014-06-24
forum: Installation &amp; Upgrades
---

### Post by Nisaar_Rahman on 2014-06-24
HI guys, please urgently assist. ive never had dual boot issues with ubuntu and windows before.
its non efi. i beleive that bitlocker is enabled on the pc and tpm is on in the bios.


Ubuntu loads fine, windows did not load. when clicking on it it goes blank then back to grub 2 secs later. tried boot repair. after boot repair when clicking on windows 8 option it then goes to blank screen with cursor blinking

[http://paste.ubuntu.com/7694214/](http://paste.ubuntu.com/7694214/)

---

### Post by grahammechanical on 2014-06-24
What mode did you install Ubuntu in? If Windows 8 is installed in EFI mode then Ubuntu has to be installed in EFI mode. 

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

