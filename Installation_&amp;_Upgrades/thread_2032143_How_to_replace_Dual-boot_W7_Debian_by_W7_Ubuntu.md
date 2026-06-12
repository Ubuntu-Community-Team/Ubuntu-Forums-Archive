---
title: "How to replace Dual-boot W7 Debian by W7 Ubuntu ?"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by JacquesFLE on 2012-07-23
Hi,

This is my first post on [http://ubuntuforums.org](http://ubuntuforums.org), I am French and I am not an expert : so some mistakes could happen from my part...

My EEE PC is on dual-boot (Grub) W7 (99 Go from 244) / Debian ((almost) the space remaining). I did not look at my Debian since a year.

I would like to  replace the Debian by Ubuntu (I will probably choose Edubuntu).

What is the safest way to do this ? Is it possible to "delete" Debian before to install Ubuntu ? How ?

Thanks a lot for your answers.

Jacques
 
ASUSTeK Computer INC. 1005HA (PBGA 437)
MS Windows 7 Starter 32-bit SP1
2,00 Go Canal-Simple DDR2 @ 266 MHz (4-4-4-12)
244 Go Seagate ST9250315AS (SATA)
Intel Atom N280  @ 1.66GHz Technologie Diamondville 45nm
Realtek High Definition Audio

---

### Post by oldfred on 2012-07-23
Welcome to the forums.

You can delete Debian with gparted but really do not have to if you just want to reuse the same partitions. Also if booting with grub from Debian, deleting it will break booting. You have to reinstall Ubuntu immediately or install a Windows boot loader to boot again.

Always best to backup before any major system change.
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


From the Ubuntu installer choose something else or manual install and choose the current Debian / (root) partition as / and what format (usually ext4). If you have a separate /home choose it but DO NOT chose to reformat it. It will automatically find the existing swap.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you want to resize Windows 7, do that from inside Windows and reboot so it can run its chkdsk and repair the resize. But do not create partitions from Windows, use gparted or the installer.

---

### Post by JacquesFLE on 2012-07-23
Thanks a lot oldfred,

I will read slowly and I will do it safely.

Regards

Jacques

---

### Post by mastablasta on 2012-07-24
talk about overwhelming informaiton...
 
But htis is the important part.
 
> **oldfred said:**
>  
From the Ubuntu installer choose something else or manual install and choose the current Debian / (root) partition as / and what format (usually ext4). If you have a separate /home choose it but DO NOT chose to reformat it. It will automatically find the existing swap.
 
 
the debian get's overwritten during install process if you chose manual paritioning and then to format the debian partition.

---

### Post by oldfred on 2012-07-24
Ok, it is a lot of info. And for some may be too much or even way too much.

And the important part is hightlighted in mastablasta post.

Some users just want the basic commands and are happy, others want detail and like links for more info and screenshots so they have a better idea of what is going to happen.

And I cannot emphasize enough how important backups or repairCD/USB are. And links to those procedures hopefully help those who need ways to backup and otherwise might skip that step as they do not know.

---

### Post by JacquesFLE on 2012-07-24
Hi mastablasta and oldfred,

Thanks for your advices,

jacques

---

