---
title: "Windows 8.1 along side Ubuntu 14.04 ON TWO SEPARATE SSD"
date: 2015-01-28
forum: Installation &amp; Upgrades
---

### Post by dj_robbie on 2015-01-28
Hello Guys,

I'm a total newbie.

I have two internal SSD's in my HTPC.

I have installed Windows 8.1 on SSD 1. 
I want to install Ubuntu 14.04 on SSD 2.

I read everywhere, guides that is based on installing Windows 8.1 along side Ubuntu 14.04 ON 1 HD/SSD.

What is the procedure for  installing UBUNTU 14.04 alongside Windows 8.1 on Two Separate SSD's ?

Thanks for all the answers i get :)

---

### Post by ubfan1 on 2015-01-28
Can you select the second SSD as  a boot device (Not that you'd have to, but if you ever think you'd move it to another machine, you might want to.)?
If you can (or might want to move it), put an EFI partition (FAT 32, 500M) on it, otherwise, just install, the first SSD's EFI partition will be used.

---

### Post by grahammechanical on 2015-01-28
Did Windows 8 come pre-installed on that machine? If so then we follow the advice given here;

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
Regards
[/LIST]

---

### Post by oldfred on 2015-01-29
If Windows is UEFI with gpt partitioning, you need to install Ubuntu in UEFI mode.

If Windows in is BIOS boot mode, you must install Ubuntu in BIOS boot mode, but can ooptionally use gpt partitioning. Windows only boots from UEFI with gpt, but Ubuntu can use either BIOS or UEFI to boot from a gpt drive if correct supporting partitions are on drive.

Often best to just disconnect one drive and install Windows, then disconnect other drive and install Ubuntu. 

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

