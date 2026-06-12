---
title: "install Ubuntu on Ultrabook Samsung series 5 with Windows 8"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by andrewbiolo89 on 2014-05-05
Hello! I am Andrea. I am Italian and I am new in this forum! I would like to install Ubuntu 14.04 ( in dual boot with Windows 8) on a laptop (ultrabook) of my friend. It is the Samsung np530u3c. I ask if someone of you has already installed Ubuntu on this pc and if there are problems with UEFI?
Thanks for the answers :).

---

### Post by oldfred on 2014-05-07
Some old Samsungs had a major UEFI bug.
 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

Others with newer systems, but maybe not your exact model. UEFI with Samsung should be similar.

 Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

See link in my signature for more info. Backups, Windows repair flash drive & reviewing instructions in first two or three links are vital. Details in link.


 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by andrewbiolo89 on 2014-05-08
> **oldfred said:**
> Some old Samsungs had a major UEFI bug.
 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

Others with newer systems, but maybe not your exact model. UEFI with Samsung should be similar.

 Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

See link in my signature for more info. Backups, Windows repair flash drive & reviewing instructions in first two or three links are vital. Details in link.


 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)


thanks for the answer! What does mean unbootable? It means "to break" the pc and the bios or that I will have to reinstall windows?? In the first step I have to deactivate "UEFI" and then  I want to clone the hard disk (and partitions) with clonezilla. 




Then I can proceed with the installation of Ubuntu :)

---

### Post by oldfred on 2014-05-08
If your model is one of those with the major bug, no,  break means it becomes a brick and has to be sent back to manufacturer.
Originally (of course) it was all blamed on Linux damaging system. But as often is the case it was the vendor has a bad UEFI and Windows can cause same issue. Not sure if you can just update UEFI/BIOS from vendor now to fix issue or not. I would do a lot of research first. And make a full backup and make regular backups all the time.

You still should be able to install to an external drive in BIOS boot mode. The issue had something to do with how UEFI stores its own data in NVRAM and it getting too full and totally locking up system.

---

### Post by andrewbiolo89 on 2014-05-08
OK! I am going to study your links :). However, I am blocked... now I understand what means "brick". I saw this bug: 
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557) 
I think that the problem is resolved and the bios is updated..I can control it. But I can't (I don't want to) risk, because the pc is not mine!

---

### Post by oldfred on 2014-05-08
If you just want to try Ubuntu, use a larger flash drive or an external drive. I might keep it in BIOS mode which is a bit more hassle to dual boot as you can only boot from UEFI/BIOS menu. But with BIOS mode you are not updating UEFI data and creating any of those issues.

This was a flash drive in both modes. i might suggest using just BIOS mode.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I have full installs in both a 16GB and a 32GB flash drive. not real speedy, but functional. Best to change some settings to reduce writes and have more RAM so most apps are working from cached RAM not flash drive once started.

---

