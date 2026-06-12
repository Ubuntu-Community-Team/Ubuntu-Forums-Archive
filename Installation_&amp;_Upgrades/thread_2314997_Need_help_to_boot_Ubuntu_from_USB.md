---
title: "Need help to boot Ubuntu from USB"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by thomas96 on 2016-02-25
Hello,

I'm trying to have W10 and Ubuntu on my MSI GE62 2QC Apache Pro.
I've 20GB free in my C: partition.

I've disabled the Secure Boot and selected UEFI+CSM boot.

But how I boot Ubuntu using my USB ?
I don't know how to show the boot menu.

---

### Post by grahammechanical on 2016-02-25
> selected UEFI+CSM boot.

If Windows 10 came pre-installed on the machine then Windows 10 would have been installed in EFI and not Bios/Legacy/CSM mode. This means that you need to load the Ubuntu live/install session also in EFI mode to install Ubuntu in EFI mode.

If Windows is installed in EFI mode and Ubuntu in BIOS/Legacy/CSM mode then we will be in a situation where one or the other of the OS will not load.

Please read the advice given here

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by oldfred on 2016-02-25
You cannot install Ubuntu inside Windows NTFS partition. There used to be wubi but that has been discontinued.

And if you only have 20GB available in your NTFS partition it may have issues. Windows NTFS partition needs about 30% free/unused space to work well. At 10% free you just about cannot run defrag and it get extremely slow.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

