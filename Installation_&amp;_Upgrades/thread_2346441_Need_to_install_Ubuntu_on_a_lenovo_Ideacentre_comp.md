---
title: "Need to install Ubuntu on a lenovo Ideacentre computer"
date: 2016-12-14
forum: Installation &amp; Upgrades
---

### Post by Supersonicx10 on 2016-12-14
Hey forum I need your help I have a new PC and need help installing Ubuntu 16.04. but i need step by step low down on how to do it. I don't think I can do it not without help not after what happened to the last one PC so yeah I need to be careful.

CPU: Intel Core i5-6400

RAM: 8GB

Video: NVIDIA GeForce GT 730

HDD: 1TB

---

### Post by oldfred on 2016-12-14
See link in my signature. I have Summary UEFI install instructions and then more explanation below if needed.

But your system will be UEFI. Key points are to only use Windows own tools to shrink NTFS partition to make space for Ubuntu and reboot immediately so it can run chkdsk. Make sure fast start up in Windows is off. And better to have fast boot off in UEFI.
And you must boot Ubuntu live installer in UEFI mode. You should get two boot options from UEFI for flash drive, one UEFI:flash drive and the other just flash drive which is then a BIOS/CSM/Legacy boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If familiar with partitions, partitioning in advance with gparted and using Something Else to install works better as you have control over sizes and any extra partitions like /home.
        
 Also shows Windows 10 screens or similar to Windows 8
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi

      [/URL]
 LENOVO Ideapad 100 Laptop 16.04 Dual Boot  
[URL="https://ubuntuforums.org/showthread.php?t=2336544"]https://ubuntuforums.org/showthread.php?t=2336544
[/URL]
 The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side 

[URL="https://ubuntuforums.org/showthread.php?t=2336544"]
[/URL] 

    [URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]
[/URL]

---

### Post by Supersonicx10 on 2016-12-15
> **oldfred said:**
> See link in my signature. I have Summary UEFI install instructions and then more explanation below if needed.

But your system will be UEFI. Key points are to only use Windows own tools to shrink NTFS partition to make space for Ubuntu and reboot immediately so it can run chkdsk. Make sure fast start up in Windows is off. And better to have fast boot off in UEFI.
And you must boot Ubuntu live installer in UEFI mode. You should get two boot options from UEFI for flash drive, one UEFI:flash drive and the other just flash drive which is then a BIOS/CSM/Legacy boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If familiar with partitions, partitioning in advance with gparted and using Something Else to install works better as you have control over sizes and any extra partitions like /home.
        
 Also shows Windows 10 screens or similar to Windows 8
[URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi

      [/URL]
 LENOVO Ideapad 100 Laptop 16.04 Dual Boot  
[URL="https://ubuntuforums.org/showthread.php?t=2336544"]https://ubuntuforums.org/showthread.php?t=2336544
[/URL]
 The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side 

[URL="https://ubuntuforums.org/showthread.php?t=2336544"]
[/URL] 

    [URL="http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi"]
[/URL]

But i'm not going to use a flash drive matter of fact, why do I need to use a flash drive?  If I shrink the drive wouldn't that turn the rest of the partitions into a dynamic disk?

---

### Post by ian-weisser on 2016-12-15
You need to use a flash drive, or some other external bootable media, because Windows cannot install Ubuntu nor partition your disks for Ubuntu.

Question: Do you intend to erase Windows and use solely Ubuntu? Or do you intend to keep Windows for occasional use?

---

### Post by Supersonicx10 on 2016-12-23
> **ian-weisser said:**
> You need to use a flash drive, or some other external bootable media, because Windows cannot install Ubuntu nor partition your disks for Ubuntu.

Question: Do you intend to erase Windows and use solely Ubuntu? Or do you intend to keep Windows for occasional use?

Sorry about not replying back soon I don't ckeck in here from time to time, to asnwer your question I want to keep windows for occasional use, it's my parent's new PC and I do not want to mess with what is pre-loaded on. We already loss the ASUS PC becuase of something I did, I don't want to it to happen again.

---

### Post by oldfred on 2016-12-23
Your old Asus may be recoverable if you have an Ubuntu live installer and can boot it on that system. If you want to try that start a new thread on that only.

You need to have flash drive(s) or DVDs as you boot Ubuntu or any system you want to install.

If you have not yet made the vendor recovery flash drive, you must do that before anything else.
I made 3 recover drives with my new Dell. One was a Dell recovery, one was a Windows recovery, and I did a full system backup with Macrium. Several DVDs and flash drives just for backups. And you need to plan on regular back ups of at least your most important data on a regular basis.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

