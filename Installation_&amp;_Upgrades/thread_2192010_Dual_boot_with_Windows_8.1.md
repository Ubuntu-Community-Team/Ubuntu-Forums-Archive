---
title: "Dual boot with Windows 8.1"
date: 2013-12-05
forum: Installation &amp; Upgrades
---

### Post by poste_d_ordure on 2013-12-05
I just got a PC (dell Inspiron 660) with Windows 8.1.  Only because I could not find a new Windows 7 machine.  I want to dual boot Ubuntu but am running into issues.  I set up a USB thumb drive as bootable drive 1 and started up machine.  It started up in ubuntu and asked me if I wanted to install Ubuntu on the PC but when I said yes, it could not find the Windows partition, said there was no OS on the machine.  It would have erased Windows, which I do not want.

How do I do this safely on my Windows 8.1 machine?

I did it on a Windows 7 machine, now dead, with no trouble.

---

### Post by oldfred on 2013-12-05
Have you turned off fast boot, that is always on hibernation.
Did you use Windows to shrink the NTFS partition and reboot? Windows has to run chkdsk after a resize.
Both hibernation flag or chkdsk flag will prevent Linux from correctly seeing the Windows install.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Lots more info in link in my signature below.

Most of the Dells we have seen have been laptops. Not sure how similar UEFI may be.

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

