---
title: "Installing ubuntu on seperate HDD?"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by michael14 on 2015-04-29
My computer has intel pentium b960 & intel hd graphics with 4GB DDR3.. I have the HDD that came with the PC and another hdd from my old laptop that is 130gb I was wondering would it work if i were to happen remove the HDD that this laptop came with (UEFI BIOS also this laptop has windows 8.0) and swap it for the 130gb hdd and put ubuntu on it and swap it in and out from time to time with the hdd with windows.. Rotate them?

---

### Post by oldfred on 2015-04-30
Some put extra drive into a USB caddy and use it as an external drive.

If system is UEFI, probably better to install Ubuntu in UEFI boot mode. 
But since totally separate drive not an absolute requirement, but still better to use gpt partitioning and include an efi partition at beginning of drive for UEFI boot. If booting in CSM/BIOS mode you need a bios_grub partition 1 or 2MB unformatted with bios_grub flag.
To convert drive to gpt you need to use gparted and first thing change to gpt.
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
Or you can use gdisk and code ef00 for the efi partition and code ef02 for the bios_grub partition.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

      [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL][https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You can skip the Windows issues since a separate drive. And if a blank drive you can use the auto install option. Any other dual boot or reinstall should only use the Something Else option.

How you boot installer flash drive UEFI or BIOS is then how it installs. So if you want UEFI you must boot installer in UEFI mode.

Skip Windows discussions and just jump to the Ubuntu install.
       But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
      [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
     
    


[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

