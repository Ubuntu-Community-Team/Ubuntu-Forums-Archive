---
title: "UEFI Ubuntu. Black screen or kernel error"
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by angelofbrokendreams on 2013-08-20
Hi everybody,
I have got a Lenovo ideapad u410 with windows 8 and uefi. I'm trying to install ubuntu 12.04.1 LTS 64bit.

I followed this guide: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

UEFI ENABLED with secure boot: 
Although I haven't got a specific UEFI boot for my pendrive like here ( [http://pix.toile-libre.org/upload/original/1347270285.jpg](http://pix.toile-libre.org/upload/original/1347270285.jpg) ), I have this ( [http://pix.toile-libre.org/upload/original/1347445084.png](http://pix.toile-libre.org/upload/original/1347445084.png) ), so I think it is allright.

Then I follow this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) from live usb, UEFI active. Boot-repair tells me to deactivate it. If I do and reboot to the live, it tells me the opposite. At the end I leave it enabled.

When the procedure ends, when I reboot grub loads, but if clicking on Ubuntu or on recovery, I have black screen. Windows is only loaded with windows boot.

Boot repair log: paste.ubuntu.com/6004981

If I disable secure boot and do everything without it and without UEFI, with boot repair, at the end I get this (see the attached picture).

Please, help me: I don't know what to do anymore and I don't want to be condemned to windows..

---

### Post by fantab on 2013-08-20
Ubuntu will install and boot fine with UEFI enabled. You have to disable neither UEFI nor 'Secure Boot'. 
I think you have Intel SRT (some sort of RAID) if the SSD came preinstalled. You have to look for Intel Smart Response Technology [SRT] in either Windows or BIOS and DISABLE it. You may also have to [disable 'fast startup' from Windows]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html") and also disable 'fast boot' in BIOS, if any.

Then reinstall Ubuntu. It will be better if you have the EFI partition on the first partition of your SSD, presently its the third and last partition on SSD. 

Some info:
[http://ubuntuforums.org/showthread.php?t=2121729&p=12539607#post12539607](http://ubuntuforums.org/showthread.php?t=2121729&p=12539607#post12539607)
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

---

### Post by angelofbrokendreams on 2013-08-20
Thank you for helping me, fantalab, first of all.
I tried disabling all those options, now i try partitioning as you sugggested. Secure boot off, uefi on, right ?

---

### Post by angelofbrokendreams on 2013-08-20
Have a doubt. Now sda1 is boot efi, sda2 hasubuntu. In the installation, i have to choose in the partitioning instrument, the device for boot loader installation. There are 2 choices that confuse me. 
1. Sda, generic.
2. Sda2, where is my ext4 with ubuntu.

Sda is correct, right ?

---

### Post by ubfan1 on 2013-08-20
Try with secure boot on first, your seeing grub on the install media with secure boot indicates you have successfully dealt with it.  When secure boot is enabled, the installer should install the signed versions of grubx64.efi and set up grub.cfg to use the signed kernel versions.

---

### Post by ubfan1 on 2013-08-20
Actually, the bootloader location for you is the EFI partition, but the default is the EFI partition on the hard disk when ANY device (not partition) is given.  sda should work.

---

### Post by angelofbrokendreams on 2013-08-20
Ok, installation complete, but it results as in the picture of my first post.
Should I try boot repair once again ? And if yes, can you advise me particular options ?

---

### Post by oldfred on 2013-08-20
Other Lenovo threads, may be similar issues.

  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.

---

### Post by angelofbrokendreams on 2013-09-01
Still didn't get it working.
Any ideas ?

---

### Post by oldfred on 2013-09-01
From UEFI menu and booting ubuntu do you get grub menu?

Then is is the black screen? Does recovery boot (second line) work?

If not sure post the link a new BootInfo report from Boot-Repair.

---

