---
title: "Replace pre-installed Windows 10 with Ubuntu 18.10 on Thinkpad E480"
date: 2018-07-30
forum: Installation &amp; Upgrades
---

### Post by haraldunlimited on 2018-07-30
I just got a Lenovo Thinkpad E480 and it came with Windows 10 pre-installed. I've been trying Windows 10 for 15 minutes and I hated it so I want to remove it entirely, replacing it with Ubuntu.

Been booting Ubuntu 18.04 from a live USB and so far it runs amazingly well. Everything works out of the box (didn't try the fingerprint scanner but also don't care about the fingerprint scanner), I have some scaling issues on high resolution but so far they are manageable. So I'm confident that I'll be fine with Ubuntu as the only hard-installed OS.

I'm not sure though how to go about the installation. The Installer recognizes the Windows Boot Manager and shows (among others) the option "Erase disk and install Ubuntu". This seems to be the most relevant to single-booting Ubuntu. Is it safe though? Worried the Thinkpad might become unbootable because this process deletes something crucial for start-up or because I missed a setting in the BIOS I should have changed in advance. Googling, I read something about disabling Secure Boot in the BIOS for example, but this only seems to apply to those who try to dual-boot their Thinkpad. Then again, the Ubuntu install wants me to configure some kind of Secure Boot if I want to install proprietary drivers (which I do) but this Secure Boot seems different than the one in the Lenovo BIOS. So I'm a bit confused about that.

Any advice on what I should look out for or if I can just straight-forward use the standard installation options under "Erase disk and install Ubuntu" would be very helpful to me. I'm completely new to installing Linux on non-Mac machines. Thank you!

---

### Post by oldfred on 2018-07-30
I would still do a full backup of Windows. Many users come back and have one application or game that they must have and it only runs in Windows. One user did post he replaces HDD with unused Windows with SSD and installs Ubuntu. Then restores unused Windows HDD and sells laptop.
If new to Ubuntu, many dual boot until they learn Ubuntu.

Standard install now is just / (root). It now uses a swap file so even a separate swap partition not required. If UEFI (Which probably is what you want) will also have ESP - efi system partition.

Somewhat more advanced users like to separate system from data, so use about 25GB  for / (root) and rest of drive for /home.  But then you do have to create partitions either during install or in advance to have separate /home partition and use Something Else install option.

How you boot install media UEFI or BIOS, is then how it installs. You should use UEFI.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
            Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
[https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi)

---

