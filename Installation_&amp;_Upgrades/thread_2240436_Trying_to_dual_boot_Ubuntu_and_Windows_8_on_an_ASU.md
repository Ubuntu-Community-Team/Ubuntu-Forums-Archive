---
title: "Trying to dual boot Ubuntu and Windows 8 on an ASUS notebook"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by Ben_Shaver on 2014-08-20
I've tried installing Ubuntu alongside Windows 8.1 using the Ubuntu installer, but there isn't the option to install Ubuntu alongside Windows, when I chose the "Something Else" option, there are multiple partitions each labelled rather random things, and are full of files, despite the computer being brand new without any previous tampering done to partitions on the computer... If anyone has some helpful input, it'd be much appreciated! :)

---

### Post by Ksiencha on 2014-08-20
Try to read through these articles: [this]("http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/"), [this one]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"), and [here]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html"). They explain how to shrink Windows partitions and how to create partitions for Ubuntu. I hope this will help :)

---

### Post by kansasnoob on 2014-08-20
Beware this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by oldfred on 2014-08-20
With UEFI and gpt partitioning, Windows does have several partitions, and system has Windows & vendor recovery partitions. So yes you have a bunch of partitions.
Only use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk and update to its new size.
Make sure fast boot is off and usually better to have secure boot off.
Make full backups of efi partition and Windows partition. If you may ever think of selling system, make DVD set of vendor image, so you can restore to as purchased.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

    
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Ben_Shaver on 2014-08-20
Thank you everyone! :p I'll read over everything and see if I can get it to work.

---

