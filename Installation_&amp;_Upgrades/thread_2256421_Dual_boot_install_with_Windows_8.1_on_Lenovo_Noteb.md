---
title: "Dual boot install with Windows 8.1 on Lenovo Notebook G50-45"
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by kagashe on 2014-12-12
I have bought new Lenovo Notebook G50-45 with Windows 8.1 today. After checking that everything is working well on Windows 8.1, I am running it on Ubuntu 14.04.1 64 Bit on USB stick. There is a small round key adjacent to power plug after pressing it I got the boot menu and selected the USB stick. Now I would like to check whether all hardware is working and I am not in a hurry to install Ubuntu in dual boot immediately, nevertheless, I require all the help to do it within next 2 days. The BIOS has UEFI Secure boot and I have not touched any settings to boot into Live Ubuntu. I have checked the partitions on the hard disk using gparted and the screenshot is inserted below. I don't understand the purpose of so many partitions.
[ATTACH=CONFIG]258515[/ATTACH]

Kamalakar

---

### Post by Ko_Char on 2014-12-12
It is here. [http://technet.microsoft.com/en-us/library/dd744301(v=ws.10).aspx](http://technet.microsoft.com/en-us/library/dd744301(v=ws.10).aspx)

3, 6 & 7 are most likely lenovo recovery

You should only touch sda5, and it is better if you partition inside Windows. Use Shrink space and leave a free space for Ubuntu (don't need to create partition). It will make life easier.

---

### Post by oldfred on 2014-12-12
Vendors do not give you recovery DVDs anymore.
And you need recovery DVD in case hard drive fails, so best to make that set now.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And you want repair tools that can boot into system, just in case.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by kagashe on 2014-12-12
Thanks for the information and all the links. I was wondering why I needed macrium but it seems it is required for full back up.

Yesterday I could not mount Windows 8 and other NTFS partitions on Live Ubuntu. Then I learned about how Windows shuts down and used the following command in Windows Run box to shutdown:
```
Shutdown /s /t 0
```

Now I can mount all NTFS partitions on Live Ubuntu. 

Kamalakar

> **oldfred said:**
> Vendors do not give you recovery DVDs anymore.
And you need recovery DVD in case hard drive fails, so best to make that set now.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And you want repair tools that can boot into system, just in case.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by oldfred on 2014-12-12
Gernerally best to turn secure boot off, you must have fast boot off in Windows and some have a fast boot in UEFI which should not be set too fast if adjustable.

Use Windows to shrink the Windows NTFS partition to make room for Ubuntu. And reboot immediately so it can run chkdsk to repair itself for its new size. Make sure fast boot is still off as Windows does like to reset itself to defaults.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lots more links in the link in my signature.

Some other Lenovo, may be similar.


 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
[http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&p=12710212#post12710212)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)

---

### Post by kagashe on 2014-12-13
Windows 8.1 was not allowing me to shrink C:/ drive less than 50%. After following the steps on [this site]("http://mindwithheart.wordpress.com/2012/11/18/windows-8-fix-you-cannot-shrink-a-volume-beyond-the-point-where-any-unmovable-files-are-located/") I could shrink C;/ drive to 10% of original size. I have left 48 GB for C;/ drive, hope it is sufficient or are there any suggestions?

Kamalakar

---

### Post by Ko_Char on 2014-12-13
If I were you, I would leave at least 60-100 GB for Windows. 
48 GB might be good for the minimum, 
but you might have a problem if Microsoft issues a major update to the system.
And Ubuntu doesn't take much space. May be 15 GB maximum. (3-6 GB for me)
The ones which are going to use a lot of space are things like videos and music.
They can be stored on either Windows or Ubuntu.

---

### Post by oldfred on 2014-12-13
The unused space inside the NTFS partition should be 30%, at 20% system starts to slow and at 10% you just about cannot do a defrag as it has no working room.
Also is going to use Windows plan on anther NTFS shared data partition. The Linux NTFS drive exposes all the hidden files & folders that Windows normally hide and users make mistakes and delete something they should not. Best to set in Ubuntu Windows partition as read only and the shared data partition as read/write.

If a new user the default install is just / (root) and swap. But if allocating a lot of GB then / can be very large. And then better to have / and /home in a separate partition. Even more advanced is a separate data partition for Linux but you need to understand partitions, ownership & permissions to set it up.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

And anything other than a default install requires you to use the Something Else install option. And if Windows not shown or reinstalling you must use something Else.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by kagashe on 2014-12-13
I have installed Ubuntu 14.04.1 on this Notebook in dual boot with originally installed Windows 8.1 without any problem. I required only two steps:
complete shutdown of Windows so that there is no problem mounting the NTFS partitions on Ubuntu and steps to resize the C;/ drive to create common NTFS partition for sharing data between Windows and Ubuntu and free space for creating ext4 and swap partitions for Ubuntu.

Kamalakar

---

### Post by oldfred on 2014-12-13
Good to hear that it all worked. :)

If you find other issues later please start another thread with that issue in the title.

---

