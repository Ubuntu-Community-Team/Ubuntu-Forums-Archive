---
title: "Booting to GRUB instead of MBR"
date: 2016-04-09
forum: Installation &amp; Upgrades
---

### Post by McTwitch on 2016-04-09
So, I just used a live CD to install Ubuntu 14.04.4 in a TB external HDD. First time I've done it in awhile. The HDD was on SDA1, and the internal drive was SDB. The installation finished, I went to restart the computer to make sure my install of Windows was all right, and it booted to a GRUB 2 screen. So somehow I need to revert the process so I can once again boot to Windows. Any and all help is appreciated.

---

### Post by McTwitch on 2016-04-09
I managed to get into BIOS and change the boot order, which let me boot to the live cd. Got back into BIOS, turned off booting to the CD, which made it boot back to the normal Windows installation. But I have absolutely no clue how to get it to boot to the new external HDD.

---

### Post by McTwitch on 2016-04-09
Upon further investigation, it would appear the problem is probably with the installation I made on the portable harddrive.

---

### Post by yancek on 2016-04-09
The standard method of installing with two operating systems on two different physical hard drives would have been to install the bootloader of the Ubuntu system to the Master Boot Record of the external drive where you installed Ubuntu.  Possible problems with this are that you may not be using MBR but UEFI.  If it is UEFI, that won't work.  Since you didn't mention which version of windows you have, there is no way for anyone here to give you practical suggestions.  Good luck.

Any BIOS should have a tab for Boot somewhere and under that a section on boot priority.  Systems are different depending upon the manufacturer of the computer or mother board so you'll have to check your user manual or post information on your hardware here.

---

### Post by oldfred on 2016-04-09
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by grahammechanical on 2016-04-09
The Ubuntu installer defaults to installing the Linux boot loader (Grub) into sda unless we tell it otherwise. But Grub should still show a listing for a Windows boot loader. Did it not do so? If not, then we are back to questions about BIOS boot system or UEFI boot system & if Windows was installed in EFI mode and Ubuntu installed in BIOS/Legacy mode.

The problem that comes with installing Ubuntu onto an external drive but its boot loader on to the internal drive is that once we disconnect the external drive we break the Grub boot loader because it looks to the Ubuntu partition for its configuration files. Which are no longer available.

Regards.

---

### Post by McTwitch on 2016-04-09
Hey everyone! I am running UEFI. It's a convoluted mess, but I figured out how to boot to the external. It takes a minute. I have to boot into Windows 8.1 running on the machine, go into settings and such, navigate to a particular area, and tell it to restart, but aim it at a USB device. Then it will restart and boot to the external. If there's an easier way, which I really, really hope that there is, I'd be glad to hear it.

---

### Post by grahammechanical on 2016-04-09
So, it is an UEFI boot system & Windows 8.1. That means that Windows 8.1 was installed in EFI mode. What mode was Ubuntu installed in? If it was BIOS/Legacy/CSM mode then you are in a situation where you can boot into one OS but not the other without going into the UEFI settings utility to make changes to the boot mode.

You need to read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I suggest that you set things up so that you can load into Windows 8.1 then re-install Ubuntu onto the external drive making sure (a) that the Ubuntu live session is loaded in EFI mode. & (b) that the Grub boot loader is going to be installed on to the external drive (sdb).

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2016-04-09
If an external drive you must partition in advance and be sure to include the ESP - efi system partition, usually as first partition.

Grub only installs to sda, but then you can copy the grub/ubuntu efi boot files from sda's ESP to sdb's ESP. And with UEFI, all systems only boot from /EFI/Boot/bootmgr.efi. So you copy shimx64.efi again from /EFI/ubuntu to EFI/Boot and rename to bootx64.efi.
Then you can directly boot external in UEFI mode from any UEFI system.

---

