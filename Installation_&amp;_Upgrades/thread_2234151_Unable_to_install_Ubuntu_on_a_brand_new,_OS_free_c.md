---
title: "Unable to install Ubuntu on a brand new, OS free computer"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by icurtisdebisschop on 2014-07-12
I recently built a computer and am trying to install Ubuntu. Whenever I try to install, it loads and loads, then reboots. I was finally able to complete an install, but it still reboots. I have tried multiple downloads of both 32 bit and 64 bit, on both USB and DVD(both created on a Mac), and nothing works. When I use a USB, I will get a few popups telling me to install, but with the DVD, it just says on the loading screen until it reboots. 

The system's specs are:
[LIST]
[*]**CPU:** AMD A10-5800K APU
[*]**RAM:** Corsair Vengeance (CMZ8GX3M1A1600C10)
[*]**HDD:** Western Digital Blue 1TB
[*]**Motherboard:** MSI A78M-E35 FM2+ / FM2 AMD A7
[/LIST]
I am starting to think something is wrong with the system, seeing as how no download works. Can anyone help me?

---

### Post by oldfred on 2014-07-12
Are you going to just install Ubuntu?
I do not know AMD systems but install should be similar.
Does system function in live mode? Booted with UEFI or booted with BIOS Mode. That may be a setting in UEFI/BIOS. Some other settings in UEFI may also be required, but not familiar with your motherboard.
Are you wanting the newer UEFI type install or the ancient but known BIOS boot install?

I do prefer to use gpt partitioning now, but Windows only boots in UEFI mode from a gpt partitioned drive.
I also prefer to partition in advance, with gparted from live installer or separate download of gparted liveCD.

If using UEFI you must have the 64 bit version. And with any new system it really should be the 64 bit.
How you boot install media, UEFI or BIOS is how it installs. Your UEFI menu for flash drive should have two options for the 64 bit version, one UEFI and one may be just the name of the flash drive.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

If UEFI:
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

If you do not have Windows just skip those steps, but shows UEFI install which is very similar to BIOS install after booting.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

