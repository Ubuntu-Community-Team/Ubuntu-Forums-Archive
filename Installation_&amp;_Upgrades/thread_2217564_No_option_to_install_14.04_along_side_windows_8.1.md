---
title: "No option to install 14.04 along side windows 8.1"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-04-17
OK, I downloaded 14.04 created a USB, booted and got the UEFI (Black) screen, started the install but no option to install along side Windows 8.1.
Went into dthe live OS off the USB and get the same. 
Not sure how to get the option to run both Windows 8.1 and Ubuntu 14.04.
I know from what I have read that I need to run in UEFI mode to run along side windows, but if I can't install along side it then it will over write windows.
Thanks to all who can help. 
By the way I am installing on a newer Asus laptop. The live USB loads and runs great. In fact I am writing this on the live OS.

---

### Post by OGpmpdog on 2014-04-17
> **irv said:**
> OK, I downloaded 14.04 created a USB, booted and got the UEFI (Black) screen, started the install but no option to install along side Windows 8.1.
Went into dthe live OS off the USB and get the same. 
Not sure how to get the option to run both Windows 8.1 and Ubuntu 14.04.
I know from what I have read that I need to run in UEFI mode to run along side windows, but if I can't install along side it then it will over write windows.
Thanks to all who can help. 
By the way I am installing on a newer Asus laptop. The live USB loads and runs great. In fact I am writing this on the live OS.

Hi There,

I dont know much about UEFI besides it sucks :)  But that aint gonna help, is it?

Have you considered creating another partition on your HD, at least 15 GB for comfortable space?  I hope that's possible in Windows Disk mgmt.  

Good Luck.

---

### Post by irv on 2014-04-17
Yes I thought about doing this with gparted, but if I do that, grub will not setup right to allow me to boot in either/or Windows/Ubuntu. I would then have to run boot repair to fix the grub if that would even work? If I am having this problem then maybe someone else has had it already and found a fix. Yes, you are right, UEFI does suck. There are a lot of users like me who are ready to give up on using more than one OS on these new computers. My old Dell was just so easy. In fact I have bought 3 of them off ebay and they just work.

---

### Post by oldfred on 2014-04-17
In Windows have you turned off fast boot or the always on hibernation?
Also is system one with Intel SRT or a small SSD to make Windows work faster?
Does Windows need chkdsk? If you resized Windows it needs chkdsk. Best to only use Windows to shrink a Windows install and reboot immediately so it can run chkdsk.

Also make a Windows repair CD or flash drive. You will need that with Windows anyway.
Make a full image backup of your Windows. If you need links on details see link in my signature.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Other Asus models, some may be similar?

 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)

---

### Post by irv on 2014-04-18
I am about to give up, no matter what I try, (turned off fast boot, always on hibernation, fast start up, secure boot), the install does not see that windows 8.1 is installed. It just tells me "This Computer currently has no detected OS." 
What I have for a system is a Asus 17-3632QM with a 2.20GHz x 8 CPU with 8 Gig of RAM. It does have a 750gig Hybrid drive. I get the black screen in Grub so I am in EFI mode which windows is running in. I really don't know what to do at this point.

---

### Post by oldfred on 2014-04-18
I do not know if hybrid drive is a new issue.

Post this from terminal in live installer.

 sudo parted /dev/sda unit s print

---

### Post by irv on 2014-04-18
This didn't work: here is what I got.

```
sudo parted /dev/sda unit s print                           
parted: invalid token: sudo
```

Edit: No matter what I type in the terminal I get invalid token:

---

### Post by irv on 2014-04-18
I tried uxterm and here is what I got.
[ATTACH=CONFIG]252187[/ATTACH]

---

### Post by oldfred on 2014-04-18
I do not know why all your data partitions are hidden. I have seen vendors do that for a second efi type partition that has extra boot .efi files for system utilities, not not normal data partitions.

Found this for Windows 7, but I do not know Windows.

[http://superuser.com/questions/459434/how-to-make-a-hidden-partition-visible](http://superuser.com/questions/459434/how-to-make-a-hidden-partition-visible)

---

### Post by irv on 2014-04-18
Every partition that is hidden is a recovery partition. The primary partition is not hidden so I don't understand why the Ubuntu install can't see it has another OS installed.
Here is the screen shot from windows.
[ATTACH=CONFIG]252190[/ATTACH]
From all the post out here it seem others are having nightmares installing on newer machine. This is really bad new for Ubuntu. It looks like new hardware manufactures and Windows are really making it hard on Linux users. It almost seem to be a conspiracy again Linux.

---

### Post by oldfred on 2014-04-18
I might just use Windows to shrink the Windows NTFS partition. Reboot so it can run chkdsk. And then use gparted to create a new ext4 partition for / (root) and a swap partition.
Then use Something Else or manual install and choose new partition for / and install.

But I would have full image backup of Windows & efi partition, and a Windows repair flash drive.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Navneet_Kumar on 2014-04-18
I suggest that u should create another partition in windows 8.1 and then install 14.04 using bootable USB in that partition and there will be no problems.

I have done the same and using 14.04 with 8.1........

---

### Post by TechAndNews on 2014-04-18
> It looks like new hardware manufactures and Windows are really making it hard on Linux users. It almost seem to be a conspiracy again Linux.

Here is a great Video Tutorial from YouTube:
[http://www.youtube.com/watch?v=LokDqte3sA4](http://www.youtube.com/watch?v=LokDqte3sA4)

YouTube Tutorial 2:
[http://www.youtube.com/watch?v=PK7gWIkAY7s](http://www.youtube.com/watch?v=PK7gWIkAY7s)

YouTube Tutorial 3:
[http://www.youtube.com/watch?v=18F3CZveMwg](http://www.youtube.com/watch?v=18F3CZveMwg)

YouTube Tutorial 4:
[http://www.youtube.com/watch?v=MWYjZ2j7HrE](http://www.youtube.com/watch?v=MWYjZ2j7HrE)

Many More YouTube Tutorials on "ubuntu install windows 8":
[http://www.youtube.com/results?search_query=ubuntu+install+windows+8+](http://www.youtube.com/results?search_query=ubuntu+install+windows+8+)

Good Luck, and Enjoy Ubuntu alongside Windows8. :)

---

### Post by irv on 2014-04-18
I am marking this one solved because I agree with oldfred the only way to install Ubuntu or any Linux for that matter is to manually shrink/run chkdsk in windows and then create a ext4 and swap using gparted and then install Ubuntu 14.04. Maybe I will have to run boot repair afterward to fix grub. For the average user this is not a way to have to do things. This will detour many from installing anything and just keep using Windows.

Edit: almost forgot to thank all who had input on this. and special thanks to you oldfred for all your help.

---

### Post by TechAndNews on 2014-04-18
> **irv said:**
>  For the average user this is not a way to have to do things. This will detour many from installing anything, by just keeping Windows. 

I agree MoneySoft may have taken steps to increase the difficulty of installing Linux onto their Proprietary Closed-Source Systems.

HOWEVER: I think we in the Linux Community need to start **Buying Pre-Made Linux Systems** (that are guaranteed to work with the included Hardware) _*and/or*_ **Building Linux Systems from Scratch** (ourselves). This building can be done by consciously _selecting Linux-Friendly Hardware_ to build our Towers or RaspberryPi Computers.

***To buy a Pre-Made Linux System, look to these Linux Vendors:***

**_ThinkPenguin_**
[https://www.thinkpenguin.com/](https://www.thinkpenguin.com/)

_**System76**_
[https://www.system76.com/](https://www.system76.com/)

_**ZaReason**_
[http://zareason.com/shop/Desktops/](http://zareason.com/shop/Desktops/)

_**EmperorLinux**_
[http://emperorlinux.com/systems/small/](http://emperorlinux.com/systems/small/)

_**PugetSystems**_
[http://www.pugetsystems.com/](http://www.pugetsystems.com/)
Select Linux as Operating System

_**LinuxNow**_-Australia
[http://www.linuxnow.com.au/](http://www.linuxnow.com.au/)

_**Fit-PC**_
[http://www.fit-pc.com/web/](http://www.fit-pc.com/web/)
Select Linux as Operating System

Hope this Helps, and Enjoy Linux :)

---

### Post by irv on 2014-04-19
For the time being I am going to run Ubuntu 14.04 off a external USB 60 gig Hard Drive. On this i7 laptop it run really fast once it it booted up. The boot time is less then a minute.
[ATTACH=CONFIG]252237[/ATTACH]  [ATTACH=CONFIG]252238[/ATTACH]  [ATTACH=CONFIG]252239[/ATTACH]

---

