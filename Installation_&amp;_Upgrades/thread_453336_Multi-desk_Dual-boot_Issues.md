---
title: "Multi-desk Dual-boot Issues"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by stroke11 on 2007-05-24
I am setting up a Windows XP SP2 / Ubuntu 7.04 (Feisty Fawn) dual-boot computer.  The computer is a Dell Precision 530 workstation that I picked up second-hand.  I had to reinstall the OS.  The machine has 3 hard drives, and I formatted them as follows:
- 20 GB IDE drive (hda - formatted as FAT32, intended as a transfer partition between WinXP and Ubuntu)
- 68 GB SCSI drive (sda - formated as NTFS, intended for WinXP)
- 68 GB SCSI drive (sdb - intended for Ubuntu)

I installed WinXP without a problem.  However, the install required me to put the WinXP MBR on the IDE disk.  I don't know why.  WinXP works fine.

I installed Ubuntu using the regular install CD.  Other than selecting the 640x480 VGA mode due to video card (ATI Radeon 7000) hang-ups and getting a warning that the Gnome theme settings could not be used, the install seemed to go fine.  I selected the guided partitioning option for the second SCSI drive.  The install completed without problem, until it was time to reboot.

The problem I have is that I cannot seem to boot into Ubuntu on the hard drive at all.  The Linux file system and files are there, but I can boot to it.  I tried using BootPart in WinXP to extract the MBR of the second SCSI disk and edit the WinXP boot.ini file on the IDE drive to enable dual-boot, but the Linux option did not work.  I tried booting into Ubuntu via the install disk and extract the files for grub onto a floppy, but I did not have success in doing that either.

Is there something I can do to enable the dual-boot to work?  Do I need to install Ubuntu differently?  Any suggestions would be appreciated.  Thank you.

---

### Post by Soybean on 2007-05-24
Were you able to add a boot option to the Windows boot menu, and that boot option just didn't work? Or is it that you don't see a boot menu, and just end up straight in Windows?

Either way, one option would be to try installing grub in the MBR on the IDE drive, overwriting Windows' bootloader. I think that's an option during Ubuntu installation, or if not, you should be able to boot from the live cd  and do it (during installation would be preferable, because it should automate away most of the potential sources of error).

---

### Post by confused57 on 2007-05-24
You might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it should be able to boot your Linux(or Windows) or reinstall grub

You can also reinstall grub with the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

