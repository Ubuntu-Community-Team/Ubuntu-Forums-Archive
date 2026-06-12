---
title: "Quadruple booting a MacPro"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Robert Elkow on 2010-03-29
I am trying to quadruple boot a MacPro with four 1 TB hard drives. I want all the operating systems, OSX Snow Leopard, Windows 7 - 64, Windows XP service pack 3, and Ubuntu AMD 64, on the first disk.  Half the second disk for NTFS data storage, half the third disk for FAT 32 storage, and half the fourth disk for LINUX storage.  I initially divided each disk in half using BOOTCAMP and then used a live Ubuntu CD with gparted to create and reformat the partitions.  On disk one partition 3 is for W7, partition 4 is for XP, and partitions 5 to 12 is for Ubuntui. I successfully installed Windows 7, and XP, and could boot into them. I made partition 5, /boot, followed by / and the others for Ubuntu.  When it asked where to put GRUB I used the pull down and /dev/sda5.  After Ubuntu was installed I restarted the computer and saw the rEFIt icons.  No Ubuntu icon!  Left to right, an Apple, Windows partition 3, Windows partition 4,legacy OS  HD, Windows in partition 3, and Windows in FAT storage.  The first two Windows partitions gave me W7 and XP as expected, the remaining 3 gave me XP.  No Ubuntu!  I then reformated the Linux partitions as ext4 and told GRUB to be installed in ((hd0,4).  After reinstalling Ubuntu still no Ubuntu icon.  Next to the Apple icon was a windows icon which booted into W7 as before, next legacy OS in partition 4 which led me to the GRUB boot menu with choices to Ubuntu, OSX, W7 in partition 3, and XP in partition 4 and a few others.  When I tried to boot XP I got the GRUB menu again.  Unable to boot into XP but could boot into W7 and Ubuntu, and I assume OSX,  the remainder two icons showed windows and legacy flags, and were labeled Windows partition 3, legacy OS in FAT storage but behaved the same giving me the GRUB menu from which I could not BOOT XP.  It looks as if GRUB overwrote partition 4? Although I told it to use partition 5.  I attempted to search for GRUB using W7 but could not find it.  

How can I install Ubuntu and get the proper icons on rEFIt and run all four operating systems without having to reinstall the MAC operating system and software?

---

