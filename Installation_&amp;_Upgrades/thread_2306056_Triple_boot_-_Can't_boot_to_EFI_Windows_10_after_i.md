---
title: "Triple boot - Can't boot to EFI Windows 10 after installing 32bit kubuntu 15.10"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by Koulache on 2015-12-11
[CENTER][SIZE=4][FONT=century gothic]Hi all
I noticed that I can not boot anymore to my Windows 10 on my lenevo G50 . Note that booting to Windows
 requires EFI mode and I've installed linux on Legacy mode ( from BIOS Setting )[/FONT][/SIZE]
[SIZE=4][FONT=century gothic]and the order of installations is Windows 10 ( Stock ) > Kubuntu > Korora

[/FONT][/SIZE]
[SIZE=4][FONT=century gothic]Notice that I've on my laptop both of kubuntu 15 (32 bits) & korora 22 next to windows 10 When I boot into legacy mode
 Hard drive is shown okay and boots to Grub ( So i can use my Kubuntu 15.04 x86 or korora 22 normally without problems ) 
but if I choose Windows 10 from grub menu it shows me a black screen with Windows boot error 0xc0000225

[IMG]http://s18.postimg.org/p23kwrt1l/12312345_723613104450083_1621143180_n.jpg[/IMG]
[IMG]http://s18.postimg.org/85ei4clhl/12386764_723613094450084_303682771_n.jpg[/IMG]

And If I swhitch into the UEFI Mode from Bios Setting , the hard drive disapears from
 boot menu ( I get only network IPV4 boot or something like that )

[/FONT][/SIZE]
[SIZE=4][FONT=century gothic][IMG]http://s18.postimg.org/u2114pyo9/12336295_723613071116753_1490639675_n.jpg[/IMG][/FONT][/SIZE]
[SIZE=4][FONT=century gothic]
I've tried to search on google for the 0xc0000225 error and tried all the methodes to fix it and they didn't 
work , and when I try to do a new installation with a Windows 7/8/10 DVD when the pc reboots after installation
 i get nothing ( the same error from Grub boot and no hard drive in EFI Mode )[/FONT][/SIZE]
[SIZE=4][FONT=century gothic]
[/FONT][/SIZE]
[SIZE=4][FONT=century gothic]When I Tried Ubuntu Live USB boot iso to perform an automatic boot repair it says :
 "You have installed on sda10 a Linux version which is not EFI-Compatible. You may want to 
install a 64-bit Linux instead"

[IMG]http://s18.postimg.org/54xnnta6h/12380533_723613134450080_1798323038_n.jpg[/IMG]

My boot options on :
Legacy Mode :
[IMG]http://s18.postimg.org/sun3ci8jt/12351106_723613157783411_737542101_n.jpg[/IMG]

[IMG]http://s27.postimg.org/3xfoc2vgj/12366803_723617967782930_672368980_n.jpg[/IMG]
[COLOR=#000000][B]When Switching to EFI Mode :

[/B][/COLOR][IMG]http://s18.postimg.org/qsmly9akp/12358448_723613087783418_123508792_n.jpg[/IMG]

[IMG]http://s18.postimg.org/6p2zm7ikp/12351272_723613051116755_1546779226_n.jpg[/IMG]
[/FONT][/SIZE]
[/CENTER]

---

### Post by grahammechanical on 2015-12-11
Your text font is much too large and those images are also very large and they make your post much to long. This kind of thing will stop people trying to help you. Anyway, you have identified the cause of the problem.

a) You have installed a 32 bit OS
b) you have installed the OS in legacy mode when Windows has been installed in EFI mode.

> 
[LIST]
[*]if the other systems (Windows Vista/7/8, GNU/Linux...) of your  computer are installed in UEFI mode, then you must install Ubuntu in  UEFI mode too. 
[/LIST]


> Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2015-12-11
Please go back and change screen shots to attachments. Not everyone has high speed Internet and you lock up their system with all the graphics.
You can attach files easily with the Forum's advanced editor and the paper clip icon.

UEFI and BIOS are not compatible. Once you start booting in one mode or the other from UEFI/BIOS you cannot switch. Or from grub menu you can only boot systems installed in same boot mode.

The standard 32 bit install does not include UEFI. Originally there was no 32 bit UEFI and a few vendors created new systems with 32 bit UEFI boot on 64 bit systems to prevent other installs. There are work arounds but not easy.

       You will need to use the 64 bit version of 14.04 or 15.04 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need Windows  fast start up (hibernation) and UEFI/BIOS fast boot quick boot UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With Something Else you can select existing / (root) on re-install. Auto install options may create new partitions.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

