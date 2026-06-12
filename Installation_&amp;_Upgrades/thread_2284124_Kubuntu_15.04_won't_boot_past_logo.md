---
title: "Kubuntu 15.04 won't boot past logo"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by mark.hilt1 on 2015-06-27
Hello I am trying to boot KDE live cd but it won't boot up in uefi mode past the Kubuntu logo and the odd time it does I cant install Kubuntu because the grub-install /dev/sda failed error comes up then installation errors any idea on how to fix this? I have redownloaded ISO image 5 times and made Live USB with rufus on windows 8.1 laptop came with windows 8.1 pree installed

---

### Post by ubfan1 on 2015-06-27
Try using a hashcheck like md5sum on the downloaded iso to confirm it is good.  Then use the media check on the CD-ROM/UWB after you create it.  That should save you some unnecessary downloads.  If the download is bad, try a torrent, that might work.
  Now you should read 
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
There are steps to take on the Windows side before the install like turning off fast boot in the power options, and getting rid of the "dynamic partitions".  Sound like the latter might be your problem.

---

