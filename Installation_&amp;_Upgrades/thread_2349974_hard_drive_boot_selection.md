---
title: "hard drive boot selection"
date: 2017-01-20
forum: Installation &amp; Upgrades
---

### Post by miro71 on 2017-01-20
Yesterday I installed Ubuntu 14.04 on my 2nd hdd hard drive, while having win8 on my main ssd drive, I turned ssd drive off at bios for installation time and I get desirable effect of computer asking me each time during startup which system I want to choose, Ubuntu or win8, with hdd drive chosen as first boot. Today I wiped everything, formatted my hdd drive and installed new Ubuntu 16.04, but this time after installation question about which system I want to choose during startup went to ssd drive, even though it was off at bios, and I'm 100% sure hard drive chosen during installation was hdd. Can you please tell me what I'm doing wrong this time and why its not working like yesterday? Thanks

---

### Post by yancek on 2017-01-20
First, you don't mention whether windows and/or Ubuntu boot.  If Ubuntu boots, go to the site below and get the boot repair software and run it per the instructions on the page and post a link to the output here.  It will show a lot more information on your system and someone should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by miro71 on 2017-01-20
The problem is, with Ubuntu installed on hdd drive, and win8 on ssd, with hdd drive off at bios I run computer and like I have no operating system, black screen like blank hard drive waiting for new system to install, where it should normally run win8 like before.

---

### Post by Dennis N on 2017-01-20
Was Ubuntu installed in UEFI mode? Is Windows installed in UEFI mode?
Creating and linking to the boot info summary results as suggested would help someone find your problem.

---

### Post by miro71 on 2017-01-20
Thanks for replies guys, here is log from boot repair

[http://paste2.org/K0wdUCZD](http://paste2.org/K0wdUCZD)

---

### Post by oldfred on 2017-01-20
You show both Windows & Ubuntu in BIOS/MBR configuration.

But it looks like Windows is hibernated or needs chkdsk. The Linux NTFS driver will not mount NTFS that is hibernated or if it needs chkdsk to prevent damage to the NTFS file structure.

Since you have two drives, best to have Windows boot loader in MBR of sda and grub2's boot loader in MBR of sdb.

If Windows updates turn hibernation on, or if chkdsk required then you may be able to directly boot sda, use f8 and use internal repair console to fix Windows.
But still best to have another flash drive with Windows repair tools or installer with Windows repair console.

While Boot-Repair usually will install a Windows type boot loader using advanced options to choose operating system and drive, if the Linux NTFS driver cannot mount the NTFS partition, then Boot-Repair does not know  you have Windows.

If Boot-Repair does not install a Windows type boot loader, you can use your Windows repair disk or from Linux use command line to install syslinux or Lilo boot loaders to MBR (not full boot loader, just MBR code).

Then in Ubuntu you can run sudo update-grub to add Windows to grub menu and set BIOS to default boot sdb. Only when Windows has issues may you need to boot sda.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)
More explanation of NTFS driver & Windows hibernation
[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation

[/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Windows screenshots:
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on) 

[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]
[/URL]

---

