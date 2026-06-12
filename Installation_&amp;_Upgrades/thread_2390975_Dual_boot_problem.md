---
title: "Dual boot problem"
date: 2018-05-04
forum: Installation &amp; Upgrades
---

### Post by nishikant.kr on 2018-05-04
Today i was trying to install ubuntu 18.04 alongside windows 10 in uefi mode on my system.For this I just created 50 GB unallocated space in C drive and boots it through USB stick. But when i tried to boot by pressing F12 and selecting USB stick in UEFI boot menu, without installing ubuntu on my system it gives the error....
Minimal BASH-like line editing is supported.For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
grub>_

---

### Post by yancek on 2018-05-04
If you can't boot the Ubuntu usb the most likely problems are a bad download of the iso or a bad burn or copy to the usb.  What software did you use to put the iso on the usb to make it bootable?

Also, I'm not sure what you mean by creating unallocated space on the C:\ drive.  THe C:\ drive is an ntfs formatted windows filesystem and you can't install Ubuntu or any Linux there.  Did you mean unallocated space on the harddrive outside C:?

Ubuntu has a documentation page on dual booting with windows 10 UEFI at the link below, read that first.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by nishikant.kr on 2018-05-04
Firstly I make sure you that i used RUFUS software to make usb bootable by choosing option GPT partition scheme for UEFI and file mode i have choosen as NTFS and yes i have created unallocated space outside c drive by shrinking that.
Please guide me if there is any problem to make USB bootable or any other problem.
Thank you...

---

### Post by oldfred on 2018-05-04
You can make an UEFI only bootable flash drive without any installer.
 UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
Or 

 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

But many have had issues with various installers, various flash drives, various ports on motherboard,  and settings in UEFI (make sure USB boot allowed or full access on).

  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
External SSD & flash drive issues  by TheFu
[https://ubuntuforums.org/showthread.php?t=2390247&p=13760330#post13760330](https://ubuntuforums.org/showthread.php?t=2390247&p=13760330#post13760330)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)

---

