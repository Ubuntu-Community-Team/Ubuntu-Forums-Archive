---
title: "How to dual boot ubuntu with windows 8  from the same hard disk?"
date: 2015-04-09
forum: Installation &amp; Upgrades
---

### Post by shamsat on 2015-04-09
I intalled the windows 8 to the first partition of hard disk in a laptop with with secure boot and UEFI options, now want to install the ubuntu 14.10 to the next partition of the same hard disk, if i install the grub2 to the MBR, is this will be possible to boot to the windows 8 from the grub menu? or there is another solution for the dual boot?

---

### Post by oldfred on 2015-04-09
MBR boot or BIOS boot is different than UEFI boot from an efi partition. The two modes are not compatible and you must totally reboot to switch modes. And you may have to turn on/off UEFI or CSM mode to match install. CSM is never secure boot. UEFI should be either secure boot or not depending on settings.
         CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

While Windows only boots in UEFI mode from a gpt partitioned drive, Ubuntu can boot either in BIOS/CSM or UEFI mode from a gpt drive. So you must boot Ubuntu installer in UEFI mode to install in UEFI mode.

Make sure Windows quick boot or always on hibernation is off, usually better to have secure boot off, but should not be required. Use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk and repair to its new size. Double check fast startup is off. If UEFI also has fast boot setting make sure that is off, or you may have difficulty getting into UEFI to change settings.

What brand/model laptop. Many have modified UEFI to only boot the UEFI entry that has Windows in the description which is not UEFI standard. But there are various work arounds to allow boot of Ubuntu/grub.

See link in my signature for lots of details & many links.


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

If Windows not shown in Ubuntu installer, only use Something Else install option.

---

