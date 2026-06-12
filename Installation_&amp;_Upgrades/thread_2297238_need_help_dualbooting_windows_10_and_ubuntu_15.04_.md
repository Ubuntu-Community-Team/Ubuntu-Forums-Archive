---
title: "need help dualbooting windows 10 and ubuntu 15.04 on new custom built PC"
date: 2015-10-02
forum: Installation &amp; Upgrades
---

### Post by happy3 on 2015-10-02
[CENTER][FONT=verdana][http://imgur.com/a/XU8Br](http://imgur.com/a/XU8Br)[/FONT]
[FONT=verdana]I tried to install it but I didn't know what I was doing so I stopped.[/FONT]
[FONT=verdana]I am booting the installation off of a USB. It is saying it is UEFI protected but should I force it? This is not a prebuilt. I just built it and installed Windows 8, then updated to 10. I just clicked continue in UFEI mode.[/FONT]
[FONT=verdana]For Picture 2, I should pick something else right?[/FONT]
[FONT=verdana]On Picture 3, /dev/sdb/ is my blank hard drive right which I should install ubuntu on.[/FONT]
[FONT=verdana]and /dev/sdc/ is the hard drive with windows 10 right because it has 3 different partitions.[/FONT]
[FONT=verdana]after selecting my hard drive, it asked me to create partition but this part confused me because there were so many options.[/FONT]
[FONT=verdana]I want to have windows and ubuntu on seperate hard drives which is why I installed an extra.[/FONT]
[/CENTER]

---

### Post by Bucky Ball on 2015-10-02
Welcome. If you've installed Win in UEFI, you need to install Ubuntu in UEFI. 

First, boot to Windows and switch off hibernation and faststart (it is called something like that). 
Boot the machine to the BIOS and switch off secure boot. 
Boot from the USB and 'Try Ubuntu'. All working on a live session and you can boot to one ok?

PS: FYI: 15.04 is supported until January 2016. You will need to upgrade to 15.10 at some time before then (and after 15.10's release in October). 14.04 LTS is a long-term support release, supported until 2019. You can upgrade LTS to LTS, leapfrogging the interim release(s) in between (next LTS is 16.04 LTS in April next year). 

The stuff in the pictures looks pretty normal for what you have done so far. Yes, you want to use 'something else' option. 

LTS releases are intended for stability and longevity. Great for production machines, servers, and any situation where you don't want to be upgrading, and possibly re-tweaking, every six months.

:)

---

### Post by happy3 on 2015-10-02
okay. If you look at the last picture, I need help creating a partition. There were too many options and I couldn't find anything online when I was on that step.

What should I pick under Use as: and Mount point

And I checked my system information and the bios mode is Legacy. So if I did not install Windows in UEFI mode, how should I install Ubuntu?

---

### Post by oldfred on 2015-10-02
Unless you want to experiment with UEFI, better to have both systems in same boot mode. If Windows is BIOS then better to have Ubuntu as BIOS boot mode.

Is Windows on sda? If not, is its boot partition on another drive? It installs its boot partition on which ever drive is set as default in BIOS. 

With multiple drives you should use Something Else as that is the only option that gives you a choice on where to install grub2's boot loader. And you want the boot loader in the MBR of the same drive as you install Ubuntu.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation
[/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
      [/URL]
 nstall 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

I prefer to use gparted for partitioning. It seems a bit easier to create partitions with, but you still have to use Something else and select change to change a partition to / & select format like ext4.

 gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[URL="https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions"]https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions
[/URL]
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

But if a new UEFI hardware system, some advantages to UEFI and gpt partitioning. If Ubuntu is on a separate drive you can use gpt and boot with either UEFI or BIOS or later easily change. But Windows only boots from MBR(msdos) partitioning with BIOS and only boots from gpt with UEFI.
Both Windows & Ubuntu install in the same boot mode as you boot installer.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)[URL="http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation"]
[/URL]

---

