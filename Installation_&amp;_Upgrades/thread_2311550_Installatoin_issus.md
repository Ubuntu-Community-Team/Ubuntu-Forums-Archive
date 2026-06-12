---
title: "Installatoin issus"
date: 2016-01-28
forum: Installation &amp; Upgrades
---

### Post by ski4 on 2016-01-28
I'm refurbishing a Hyper threading P4 system with Win7 Ultimate installed........6GB DDR2 Ram, 500GB HDD....I'm wanting to partition and install Ubuntu 14.04 x64 as a duel boot...75GB for Win7.......75Gb for Ubuntu the rest for video's, music, Photo's...whatever.....so from 500GB.......75Gb for Win, 75Gb for Ubuntu,that leaves 350Gb as storage.......I've tried Win7 Partitioner and Ubuntu Install Partitioner with no luck......Ubuntu just won't install or I'm choosing the wrong Partition......so I'm having trouble with that...........any advice????????

---

### Post by Bucky Ball on 2016-01-28
Boot from the Ubuntu install media. Choose 'Try Ubuntu'. At the desktop launch Gparted. Make 75Gb _free space_ where you want to install Ubuntu. Don't waste time creating partitions for it. Windows can't create partitions Ubuntu can be installed to in any case. 

When installing Ubuntu, choose 'Something Else' at the partitioning section and create a partition for Ubuntu with the free space and with the mountpoint / (will be selectable as a default there). You will also need a 2Gb /swap partition somewhere. That is it. 

If you are storing all your personal files on a /data partition (and NTFS partition called whatever you like that is shared by both Win and Ubuntu) then you don't need anything like 75Gb for Ubuntu. 25Gb would be ample, and probably more than enough. Win7 uses about 40Gb from memory and same there. If your personal data is on another partition, you don't need 75Gb. So, if you're installing the OSs only to their partitions and keeping your data to share on a separate partition, then something basic would be

Win (NTFS): 40Gb
Ubuntu (/ and EXT4): 25Gb
/swap: 2Gb (swap partition has an option 'swapspace' rather than a filesystem type like 'EXT' or NTFS which will be selectable in the installer's partitioner). 
/data (NTFS): Rest of space on disk.

Note well: If you install Win (install Win first) in UEFI mode, then Ubuntu MUST be installed in that mode too. Ditto for legacy. Whatever mode Win is installed in, Ubuntu goes the same way. Good luck and hope that helps.

---

