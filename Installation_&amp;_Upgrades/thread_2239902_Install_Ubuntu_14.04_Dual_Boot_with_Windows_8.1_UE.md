---
title: "Install Ubuntu 14.04 Dual Boot with Windows 8.1 UEFI BIOS"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by rickm1945 on 2014-08-16
I have Ubuntu 14.04 on a usb HD, but would like to Install Ubuntu14.04 in a dual boot with Windows 8.1. I have done this with other Windows Version but UEFI is a new deal for me. I know how to shrink Hd etc. ad I would like to install using "Something Else" and saw one istall method say use Root, Swap and Home. Before I did / /root /swap /home. Which is the best way to install. I want to dual boot window to give choice of Ubuntu or Windows. Can this be accomplished without any problems?

---

### Post by oldfred on 2014-08-16
Depends a lot on hardware and vendor. UEFI has added complications as now instead of just BIOS, you have to choose between UEFI, UEFI with secure boot and BIOS emulation or CSM/Legacy modes. And how you boot is how you install as the modes are not compatible. 

Then newer hardware with dual video or Intel SRT with small SSD add even more issues if a high end laptop. A few early UEFI that had Windows 7 did just install in UEFI mode without hardly any more issues than you got with BIOS.

As always really good backups are essential. And a bug or two or user error may erase entire drive, or only use Something Else.

There is / (root) and swap which is the default install. But either separate /home or data partition(s) are often suggested.

Many useful links in the link in my signature. 

Be sure to shrink Windows with Windows own tools and reboot so it can run chkdsk and update to its new smaller size. Then make sure fast boot or the always on hibernation is off. Usually better to install with secure boot off, but Ubuntu will work with secure boot on. Grub currently does not boot Windows from its menu with secure boot on, but you can use one time boot key or UEFI/BIOS to select which system to boot.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

      
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

---

### Post by rickm1945 on 2014-08-16
I have the UEFI Set but secure boot I can't disable. Does have a menu for running other OS that doen't support Secure boot, so I enabled it. I don't understand the the efi, sorry but I'm lost on that one. I paln on using 400 GB of my 1TB Hd for Ubuntu. 33,000MB for swap /root 21000 and the rest of partition for /home. does that sound ok?

---

### Post by oldfred on 2014-08-16
There should be 3 configurations, but some UEFI have only two switches. Microsoft requires vendors to configure UEFI to allow turning off secure boot unless it is a tablet type device which then may not have any user settings.
You should have UEFI on, UEFI on with secure boot and UEFI off. And UEFI off should be BIOS/CSM on. But some just have UEFI meaning secure boot, and BIOS or UEFI depending on what is found on hard drive to boot from.

I would not make swap very large. You only need swap equal to RAM in GiB if you want to hibernate, but Ubuntu boots fast enough that hibernation only gives minor speed boost on booting but added issues and complexity.
Typically I suggest 2GB for swap if you have 4GB of RAM or more. Then 25GB for / (root) and the rest for /home and/or a shared data partition. There is no /root nor /swap. It is just / , swap and /home when you use something else and select what to mount a partition as. Best to use ext4 for / & /home. Swap has no format.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Always create a good backup of Windows and the efi partition before install and particularly before a reinstall.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

            Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by rickm1945 on 2014-08-17
Thank you oldfred for your help. I have Ubuntu 14.04 running flawlessly on my 160GB Toshiba External HD. I thought the dual boot might be better but after seeing what is involved I think I may just leave my Ubuntu 14.04 LTS on the USB external Drive. I may get a larger , 500GB USB Drive to put it on for more room. What are your thoughts on this? Thanks again for your help.

---

### Post by kansasnoob on 2014-08-17
Beware this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by rickm1945 on 2014-08-17
Thanks for the info. I primarily use Ubuntu 14.04 and prefer it over Windows 8.1 which sucks. I really like Unity and rarely use Windows. I always use "Something Else" when installing Ubuntu, I like a clean install, guess  I got that from  all the bad things that happen in Windows when you don't do a clean install.

---

### Post by grahammechanical on 2014-08-17
I would say that the information given above is applicable whether we are installing Ubuntu on the same disk as Windows 8 or on a separate disk. And you have already done that. It is the motherboard that has UEFI and secure boot and GPT and all that stuff. And there is an advantage to installing on separate disks. If one HD fails you still have a working system and a place of local backup.

Any difference would be between the data transfer rates of the two hard disks. So, if Ubuntu performs comparatively well on that external HD then why change? Unless putting it on the main HD would improve performance, 

Regards.

---

### Post by oldfred on 2014-08-17
The size of drive you may need depends just on what you do. And how large the data you save and accumulate is.

My system has a 60GB SSD, two 160GB drives from original build in 2006 and an added 640GB drive. But I can copy all the real working bits to my old laptop when I travel that only has a 160GB drive and the now unused XP still takes up some of that. A lot of my space is just other test installs.

---

