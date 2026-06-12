---
title: "help with dual booting"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by justinbeal60 on 2015-07-04
Ok well when I try to install Ubuntu it doesn't read my windows 8.1. So I cant install it beside my windows in its partition. Now that's fine I made a separate partition and it will let me install it on that but im scared to because if it installs it to that separate partition from windows. Even though I still have the windows partition. Will it not recognize the dual boot since its not reading windows 8.1 partition to add Ubuntu beside it. So my question is will it not read my windows 8.1 after I install it on the new partition? or will it and its not letting me install it in the same partition as the windows one  which I don't want to is just to a bug? and that's why its not reading that I have windows 8.1 installed.

---

### Post by oldfred on 2015-07-04
Have you turned off fast start up in Windows. That is main reason Linux cannot see a NTFS partition. It can also be that the NTFS needs chkdsk, which it also does after a resize.

Also make backups of Windows. My new Windows system suggested a Windows backup, a Dell backup & I made a full backup with Macrium.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

      It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen. If Windows is UEFI and Windows 8 pre-installed always is UEFI, you need to install Ubuntu in UEFI boot mode. And how you boot installer/liveDVD/live Flash is how it installs. So boot in UEFI mode.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Many more UEFI links & details on installs in link in my signature below.

---

### Post by justinbeal60 on 2015-07-04
> **oldfred said:**
> Have you turned off fast start up in Windows. That is main reason Linux cannot see a NTFS partition. It can also be that the NTFS needs chkdsk, which it also does after a resize.

Also make backups of Windows. My new Windows system suggested a Windows backup, a Dell backup & I made a full backup with Macrium.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

      It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen. If Windows is UEFI and Windows 8 pre-installed always is UEFI, you need to install Ubuntu in UEFI boot mode. And how you boot installer/liveDVD/live Flash is how it installs. So boot in UEFI mode.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Many more UEFI links & details on installs in link in my signature below.

Well I checked for errors and there was none I also turned off fast startup in windows and it didn't fix the problem.

---

### Post by oldfred on 2015-07-04
What version of Ubuntu?
While usually best to install LTS verisons, very new hardware may need newest version to have latest drivers.

You should then use Something Else. If Windows is not seen with an auto install option then it may overwrite it.
If you use gparted does it show NTFS partitions. Then you can create partitions /, /home & swap. The use Something else and choose those partitions with the change button.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
      
 Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support)

---

### Post by justinbeal60 on 2015-07-04
> **oldfred said:**
> What version of Ubuntu?
While usually best to install LTS verisons, very new hardware may need newest version to have latest drivers.

You should then use Something Else. If Windows is not seen with an auto install option then it may overwrite it.
If you use gparted does it show NTFS partitions. Then you can create partitions /, /home & swap. The use Something else and choose those partitions with the change button.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
      
 Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-support)

Hey I got a question Im gonna try to dual boot it. Now to restore my pc idc if I lose my files doesn't matter to me. Now my question is I have a oem system windows 8.1 I have a cd with iso. Now if something goes wrong with the download can I format the whole hard drive and just reinstall windows 8.1 and use my product key to re enable it. Because idc about losing my files.

---

### Post by justinbeal60 on 2015-07-04
I got ubuntu to work i just installed it even though it wasn't reading my widows 8.1 but luckily the only thing i have to do is go to bios and switch the order of the ubuntu and windows which ever one i want to use for 1st and then it will start up everytime using that os. So i have both os now its a little more work then just choosing which one but its all good. Actualy as i wrote this i was on ubuntu 14.04 so im happy. But still thanks for the help.

---

### Post by oldfred on 2015-07-05
You can change to solved if issue is resolved.

If you want to change boot orders, is it UEFI or grub. You have two boot managers that present menus. Usually UEFI is set to boot ubuntu entry and grub offers to boot everything.

       sudo efibootmgr -v 

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
      
 Change boot order with efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)


Grub menu  
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

---

