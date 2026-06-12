---
title: "Interesting Problem...."
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by Badams130 on 2011-01-17
So i finally installed Ubuntu 10.10 on my laptop which came preinstalled with Windows 7 64bit. When i went to shrink the Windows partition, Windows' Disk Managment tool indicated that there were three partitions on my Hard Drive (prior to creating a Ubuntu partition), i was told this wasn't a problem so i shrunk the C: drive and created ~60Gb unallocated space for Ubuntu. From here i basically followed this: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) except i didn't create a "Storage" partition, just one partition for Ubuntu. If it matters: mount point was "/", file system was Ext4, and i put the new partition at the "end".

 Ubuntu installed fine and ran perfectly, however on the Grub menu, there were several options: two were for Windows 7, one was for Vista(?), and two were for Linux. The first time i booted up (using the second Windows 7 option) Win7 it ran seemingly perfectly, but i had to restart because my Anti-virus updated. The 2nd time it ran (same boot option), Windows command prompt crashed on start-up and i wasn't able to run any programs aside from minesweeper (but start-up programs appeared to have started up). Eventually i was able to run Firefox after setting its compatability mode to Windows XP SP2 and running as an admin. I tried the other Windows 7 boot option but that didn't solve anything.

I know thats alot of text to read, but please help! [-o<

(also, i am uninstalling my Anti-virus now to see if thats what caused my problems)

---

### Post by Badams130 on 2011-01-17
it must have been my Anti-virus because things are running smoothly now #-o but i still would like to know why there is a Vista boot option on GRUB, if that's something i could get an answer to.

Thanks for all the help

---

