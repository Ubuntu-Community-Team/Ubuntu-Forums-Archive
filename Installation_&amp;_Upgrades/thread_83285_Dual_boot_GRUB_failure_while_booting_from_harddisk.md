---
title: "Dual boot GRUB failure while booting from harddisk"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by malluguy on 2005-10-28
Hi guys,

Last night I installed 5.10 on my Laptop. I managed to go through the installation without any problems at all. When prompted for grub, I installed it. The problem occurs when I try to boot the machine from hard disk. I get a blank screen with GRUB on it. I do not even get the grub> prompt.

I was able to boot my machine with a Suse 9.2 CD that I had. When booting from the CD, grub recognizes my OSs and I am able to start both breezy badger and XP.

For information here is my partition information

#1 /dev/hda1 60GB     NTFS
#3                14.5GB  ext3
#5                700MB   Swap

Any help would be appreciated.

---

### Post by malluguy on 2005-10-29
any help guys? I am still struggling to resolve it. I reinstalled it 3-4 times.

Should /boot be the first partition in my disk? Is it related to my BIOS where it can not read past cylinder 1024 (LBA?)

---

### Post by darth_vector on 2005-10-29
perhaps this isnt the optimal answer but:

try reinstalling with a similar partition sheme, but make a /boot partition as a primary partition (swap and / can be logical), and make sure you set the bootable flag. also make sure that grub is installed on the MBR.

---

### Post by XBlade on 2005-10-30
I had the same problem, didn't solve it however I found that switching boot drives was an alternative for me as it can be done thru bios with the 2 raids I have setup - only problem was that I had to install ubuntu on the SATA raid rather than the SCSI raid like I wanted.

One thing that I found interesting was that during the testing I had installed a 3rd party bootloader, when I tried installing Grub over the top of it the bootloader still started first(corrupted as it was).

This was with Ubuntu 64.
RAID Array 1 - 
 1#SCSI HDD NTFS 45gb windows
 2#SCSI HDD EXT3 and SWAP partitioned between 19gb 
RAID Array 2 - 
 1#360 SATA
     ^^^ -- installed linux here instead and reconfigured SCSI for windows only

---

