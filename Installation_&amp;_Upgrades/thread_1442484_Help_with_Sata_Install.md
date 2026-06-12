---
title: "Help with Sata Install"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by kalisto2002 on 2010-03-30
Ok so im not a complete linux newbie but i have never messed with sata drives and definitely not fakeraid, but my problem is every time i try and install ubuntu 9.10 it will not load grub and it funks off my windows boot loader. When GRUB trys to boot, it boots to emergency grub and it cant find the partition, but if i look at it with the live cd it sees the partition just fine, heres a list of hardware, please help me out i want to go to Linux and Windows XP.

AK77-600 Max Motherboard
1.5 GB ram
Promise Fasttrak 378 Raid Controller
1x120gb sata harddrive
1x40gb sata harddrive
both harddrives are setup in a stripe 0+1 raid setup (two seperate drives)


Please help me out

Thank You





Ok so i found a solution by searching all the forms not just the installation and upgrade form.
Here it is

Booted from CD
Choose the F6 + nodmraid option
Choose "Install Ubuntu" option (not the Live enivronment)
Before getting to the partition I switched to a tty session using CTRL+ALT+F1 and ran "sudo apt-get remove dmraid"
After this I was able to see the drives, and install to them.

---

### Post by carnytom on 2010-03-30
Solution ????????

---

