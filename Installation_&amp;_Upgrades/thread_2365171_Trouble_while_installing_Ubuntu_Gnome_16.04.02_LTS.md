---
title: "Trouble while installing Ubuntu Gnome 16.04.02 LTS on new HDD"
date: 2017-07-03
forum: Installation &amp; Upgrades
---

### Post by doolosbekov on 2017-07-03
Hello guys! I'm here a new as a beginer, so my question for most users of this forum, should be easy so.

About a few days ago, I decided to use Ubuntu, as an alternative OS to my previous Windows 10 OS. 

I downloaded and burdend bootbale flash-drive with Ubuntu Gnome, but I can't instaling the OS, becouse of GRUB error.

The warning said that the GRUB can't install becouse of: 

*Failed to install package 'grub-efi-amd64-signed' in /target/". Without the GRUB bootloader, the installed system will not boot.

Help me solve this issue!

And also from other forums, guys said that my HDD markups is wrong so I paste my markup also here.

1=>> EFI   > 512 MB > FAT32
2=>> /     > 60  GB > EXT4
3=>> /home > 60  GB > EXT4
4=>> SWAP  > 16  GB > LINUX-SWAP
--------------------------------
5=>> /meida/local_drive_1 > 280 GB > EXT4
6=>> /meida/local_drive_2 > 280 GB > EXT4
7=>> /meida/local_drive_3 > 280 GB > EXT4


FREE SPACE=>> 23 GB

---

### Post by yancek on 2017-07-03
The link below is the official Ubuntu documentation, scroll down to the section "Installing Ubuntu in UEFI mode" as the info you posted shows that you already have an EFI partition.  Your installer should create the neccessary EFI files in that partition under an ubuntu directory.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

