---
title: "Ubuntu 14.04 installation in Lenovo A-740"
date: 2016-10-10
forum: Installation &amp; Upgrades
---

### Post by satendra0786 on 2016-10-10
Dear Ubuntu People,

Could you please guide me how to install ubuntu in LENOVO A740 Desktop(All in one machine)? 

Thanks,
SK

---

### Post by mörgæs on 2016-10-10
Hi, welcome to the fora.

I would not count on old software like 14.04 on new hardware. Better to try 16.04.1 in a live boot as a first step.

---

### Post by RobGoss on 2016-10-10
Welcome to the forum. 

If this is your first time using Ubuntu I recommend do some research before you get started there's a lot that is required. 

This guide might help you a few questions you might have
[https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Install_Ubuntu)

Each installation maybe different and may need a different  approach depending on the machine and the hardware I think Lenovo's may fall in that category

---

### Post by oldfred on 2016-10-10
Looks like an UEFI system, so be sure to install in UEFI boot mode.
Use Windows to shrink NTFS partition, reboot so it can run chkdsk.
Turn off fast boot in UEFI, at least until reconfigurations done, otherwise can be difficult to get into UEFI to make changes.
Turn off fast start up or always on hibernation in Windows.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
      
 Also shows Windows 10 screens or similar to Windows 8
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi
      [/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

Lots more details in link in my signature.

Looks like you have nVidia.
You may need nomodeset on install and first boot or until you install nVidia proprietary driver from Ubuntu's repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

