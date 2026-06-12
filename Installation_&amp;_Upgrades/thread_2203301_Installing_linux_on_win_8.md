---
title: "Installing linux on win 8"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by jabbe-duck on 2014-02-02
Hey. So im intrested of installing Ubuntu on my laptop. I have a Acer 5750G with windows 8 installed.
So ive read much about the problems with UEFI and so on on Windows 8 machines. 
I have found out that my computer doesnt have UEFI,  its a bit old for that, i only have regular BIOS.
So i wonder now, i want to install unbuntu. Is it safe to install through wubi? Or should i format and partition my HDD and install ubuntu on one side, and windows 8 on the other ?? 
Would really llike som advice :D

---

### Post by tfrue on 2014-02-03
Never use WUBI! It's deprecated and not recommended to use for partitioning.

Boot into Windows and shrink the drive to allocate as much space as you would like for your Ubuntu installation, like 15-20GBs.

Once that is finished, live boot into Ubuntu with a CD or USB, then click "install", and be sure to choose "Something Else" when you get to the partitioning section and choose the space that you allocated for Ubuntu, and be sure that the drop down box asking about installing Grub is pointed to /dev/sda.

Be sure that the installer can see Win 8, if it doesn't give you an option to install alongside Windows, then I would wait and we can take the appropriate steps to heading in the right direction.

Let it finish installing and you should now be able to dual boot your laptop with Win 8!

---

### Post by jabbe-duck on 2014-02-03
> **tfrue said:**
> Never use WUBI! It's deprecated and not recommended to use for partitioning.

Boot into Windows and shrink the drive to allocate as much space as you would like for your Ubuntu installation, like 15-20GBs.

Once that is finished, live boot into Ubuntu with a CD or USB, then click "install", and be sure to choose "Something Else" when you get to the partitioning section and choose the space that you allocated for Ubuntu, and be sure that the drop down box asking about installing Grub is pointed to /dev/sda.

Be sure that the installer can see Win 8, if it doesn't give you an option to install alongside Windows, then I would wait and we can take the appropriate steps to heading in the right direction.

Let it finish installing and you should now be able to dual boot your laptop with Win 8!

Okey . Awesome thanks ;) No WUBI then :D 
When you say shrink the drive ? Do i need to format my windows 8 then ? Or is it just possible to shink the drive as you say and still keep windows 8 ? In that case it would be awesome ;)

And there should be no problem with UEFI, because i dont have it? :D 
Yes ;D

---

### Post by Mark Phelps on 2014-02-03
Don't just charge into installing side-by-side with Win8 using the installer.  This risks corrupting Win8 and rendering it unbootable. Use only the Win8 Disk Management utility to do any Windows partition resizing.

---

### Post by tfrue on 2014-02-03
In Windows, use the Disk Management utility to partition the drive as that will be the best way to partition a HDD with Windows on it. I think you could type keywords like: partition, shrink, or disk manager as the tile screen and go to the settings tab and you should be able to go to it there. 

While in the Disk Management tool, you will specify how much space you want to shrink, to determine how much space you will allocate yourself, and then you can leave it un formatted and un initialized since Ubuntu will do what it does when it comes time to install.

You can keep Windows 8 so you do not have to remove it and Ubuntu will happily live with Windows! :)

Good luck,
Chris

---

### Post by jabbe-duck on 2014-02-03
> **tfrue said:**
> In Windows, use the Disk Management utility to partition the drive as that will be the best way to partition a HDD with Windows on it. I think you could type keywords like: partition, shrink, or disk manager as the tile screen and go to the settings tab and you should be able to go to it there. 

While in the Disk Management tool, you will specify how much space you want to shrink, to determine how much space you will allocate yourself, and then you can leave it un formatted and un initialized since Ubuntu will do what it does when it comes time to install.

You can keep Windows 8 so you do not have to remove it and Ubuntu will happily live with Windows! :)

Good luck,
Chris

Okay ;) I think i understand ;)
So this way windows wont get partitioned, it only shrink its C: and make another partition E: with the size you give it ;) 
And in that new partition i install ubuntu ;) Yes, hopefully without any trouble.
What if my computer cant se my windows 8 installation? In case? not expecting it thought
Yeah, one more thing. I am going to be able to install the latest 13.10 ubuntu? And not the 12.04=

---

### Post by oldfred on 2014-02-03
DO NOT create partitions with Windows. It may convert to dynamic partitions from its standard basic partitions. And dynamic does not work with Linux and has no easy undo.
Linux does not work on any Windows formatted partitions, although you can read & write from NTFS.

If you have not used all 4 primary partitions Ubuntu should just install side by side to Windows in the un-allocated space.
But do full back ups of Windows and make a repairCD or flash drive for Windows. Some users are picking the wrong install option and that erases the entire drive.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by jabbe-duck on 2014-02-03
Ahaa .D Yes, So far i have splitted my C drive to a 25gb un-allocated space in W D M. 
So if i am correct, i should plug in the bootable usb drive, start live ubuntu, choose install>something else> choose the un-allocated space and choose in the dropdown menu dev/sda? 
? 
But i will make a backup of windows now anyway, just in case. How much does it need on my hdd or usb drive ? dont have any discs at all here.  i upgraded windows 8 so i only have 2 extra partitions connected to my C. one called faultless (resetpartition,) and reserve. And then of course my C drive.

---

### Post by westie457 on 2014-02-03
[B]Do not install yet.
[/B]
There might be an issue with the number of partitions on your hard drive.

Please boot using the LiveDVD/USB in 'Try' mode that is 'Try without installing'.

Once you have the Live Desktop on your screen open a terminal (pressing Ctrl+Alt+T at the same time).
Type in ```
sudo fdisk -l
``` and hit Enter.

Post the output of that command here for further assistance.

The l in the command is a lower-case L not a 1 or i

---

### Post by jabbe-duck on 2014-02-03
> **westie457 said:**
> [B]Do not install yet.
[/B]
There might be an issue with the number of partitions on your hard drive.

Please boot using the LiveDVD/USB in 'Try' mode that is 'Try without installing'.

Once you have the Live Desktop on your screen open a terminal (pressing Ctrl+Alt+T at the same time).
Type in ```
sudo fdisk -l
``` and hit Enter.

Post the output of that command here for further assistance.

The l in the command is a lower-case L not a 1 or i

Okey. Here it goes.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc1ce73dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    37750783    18874368   27  Hidden NTFS WinRE
/dev/sda2   *    37750784    38467583      358400    7  HPFS/NTFS/exFAT
/dev/sda3        38467584  1413943295   687737856    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1052 MB, 1052639232 bytes
26 heads, 57 sectors/track, 1387 cylinders, total 2055936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe25a021b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     2055935     1027936    6  FAT16

Oh yeah. I have done a Windows 8 repair USB now . I noticed some files called UEFI and bootx64efi or something

---

### Post by westie457 on 2014-02-03
You look good to go ahead with the installation.

Personally I would boot back into Windows and shrink the C:\ drive by as much as Windows will allow. you should be able to get as much as an extra 100 GB of space. Even more if you disable all forms of hibernation.
I do not know if a non-uefi windows 8 installation defaults to 'Fastboot' - a form of hibernation. No harm in checking this in the Power Options found in the Control Panel. It is very important that Windows is completely shut down before you install another operating system.

One very helpful thing about running the installation from the Live Desktop is you can use the internet and other things. So if you see something you are not sure of, fire up that browser come back here and ask your questions.

Hope this helps and good luck.

---

### Post by jabbe-duck on 2014-02-03
> **westie457 said:**
> You look good to go ahead with the installation.

Personally I would boot back into Windows and shrink the C:\ drive by as much as Windows will allow. you should be able to get as much as an extra 100 GB of space. Even more if you disable all forms of hibernation.
I do not know if a non-uefi windows 8 installation defaults to 'Fastboot' - a form of hibernation. No harm in checking this in the Power Options found in the Control Panel. It is very important that Windows is completely shut down before you install another operating system.

One very helpful thing about running the installation from the Live Desktop is you can use the internet and other things. So if you see something you are not sure of, fire up that browser come back here and ask your questions.

Hope this helps and good luck.

Ah :D I appriciate all the help i got :D 
Okey so i would be ready to go then :D Yeah going to fix a bit bigger partition for ubuntu, like 50gb instead :)

But when i have installed ubuntu? Then i have got ubuntus grub menu instead of Windows Boot Manager?
Anyway to get that back or is it grub? When i install it, and reboots and dont find Windows 8 ? What should i do then? Just in case :D

---

### Post by westie457 on 2014-02-03
When Grub gets installed to the MBR of the first hard drive something called 'os-prober' should find the boot files for Windows. When you start the computer you should get a menu with some options. The first one should be Ubuntu, the second should be advanced options. There will be others and Windows will be at the bottom of the list.

If it goes right to Ubuntu without the menu showing at all, this is easy to fix.

If it boots to a black screen this is usually easy to fix as well.

Let us know how it goes.


ps Welcome to UF

---

### Post by jabbe-duck on 2014-02-04
> **westie457 said:**
> When Grub gets installed to the MBR of the first hard drive something called 'os-prober' should find the boot files for Windows. When you start the computer you should get a menu with some options. The first one should be Ubuntu, the second should be advanced options. There will be others and Windows will be at the bottom of the list.

If it goes right to Ubuntu without the menu showing at all, this is easy to fix.

If it boots to a black screen this is usually easy to fix as well.

Let us know how it goes.


ps Welcome to UF

Ahaa .
So one more thing before i feel safe to install ubuntu, look at this picture i linked. How should i do the partitioning.

[http://postimg.org/image/i96if37ff/](http://postimg.org/image/i96if37ff/)

So i we say i would install it now, just saying. IN that case i would have choosed the free space just because when i did the shrinking of the volume in windows i set it at 50gbs, and that space there is 50gb +. So i supposed it is that space i want to choose.? And Then?

---

### Post by westie457 on 2014-02-04
If you are not given the chance to create an 'extended partition' or 'Logical partition' when creating your 'root/home partition **_STOP_**.

From your screen shot.
Select 'free space' click 'New' - a window opens - in this window top box will say 'Primary' click here and select 'Extended/Logical' cannot remember the exact words.
Place this at the start.
You will set this partition to 'ext4'
Next box is for the size, use all apart from about 2Gib, under this box is a small box, fill this to format.
Next box is for the mount point, put a ' / ' in here.
Click 'Done' Another window opens with a warning 'Changes must be written to disk'. Before pressing 'continue' were you given the chance to create a logical partition. If not,******_STOP _**cancel the installation.

Now click 'New' again, select 'logical' and 'use as Swap'. Click done, continue with the installation.

**See you on the bright side.**&#8203;

---

### Post by jabbe-duck on 2014-02-04
> **westie457 said:**
> If you are not given the chance to create an 'extended partition' or 'Logical partition' when creating your 'root/home partition **_STOP_**.

From your screen shot.
Select 'free space' click 'New' - a window opens - in this window top box will say 'Primary' click here and select 'Extended/Logical' cannot remember the exact words.
Place this at the start.
You will set this partition to 'ext4'
Next box is for the size, use all apart from about 2Gib, under this box is a small box, fill this to format.
Next box is for the mount point, put a ' / ' in here.
Click 'Done' Another window opens with a warning 'Changes must be written to disk'. Before pressing 'continue' were you given the chance to create a logical partition. If not,**_STOP _**cancel the installation.

Now click 'New' again, select 'logical' and 'use as Swap'. Click done, continue with the installation.

**See you on the bright side.**&#8203;

Ahaa :) Thanks man ;) About "Click 'Done' Another window opens with a warning 'Changes must be written to disk'. Before pressing 'continue' were you given the chance to create a logical partition. If not,**_STOP _**cancel the installation."

If im given a chance to create a logical partition then i continue, if not will STOP. And then again start by pressing New and then i am able to select logical and use as swap? Correct ? I think im ready :) Whats the worst thing that can happen? Windows disapears, but i would still be able to use Ubuntu? :D

---

### Post by westie457 on 2014-02-04
As long as you create the Extended/Logical partitions everything will be fine.
The worst that can happen is a meteor hitting this planet.
On a computer the worst is accidentally wiping Windows and Ubuntu or another OS not installing.

---

### Post by jabbe-duck on 2014-02-04
Hm okey. ****. Tried but i didnt understand the exact.
When i come to to partition screen, the only way to get forward is to press on the space on the screen and then press the + at the left ? 
In there i say where it stood primary and so on. So im able to choose logical, but i didnt quite understand the second part. In a dropdown menu there was something started with ext4, ......, and under theres a headline "Mount", and there should i do what? Sry if am a total noobie, just dont want to **** up my pc. xD

---

### Post by oldfred on 2014-02-04
You have to choose change to an existing partition if it exists, usually only if a reinstall or you partition in advance or + to add a new partition. 
Each partition need to have a size, whether logical or primary, a format like ext4 and a mount point like / (root), /home, swap (no format) etc.
Logical and primary does not apply to gpt partitioned drives which all new UEFI systems have. All logicals must be inside one extended partition. But only if formatting in advance with gparted do you see all those extra details.

Default installs are just / & swap, but if manually creating partitions you can add /home which is often suggested or many other partitions that often are only required for servers or advanced installs not average desktop installs.

My screen shot show me reusing an existing partition with an old install.

---

### Post by jabbe-duck on 2014-02-04
> **oldfred said:**
> You have to choose change to an existing partition if it exists, usually only if a reinstall or you partition in advance or + to add a new partition. 
Each partition need to have a size, whether logical or primary, a format like ext4 and a mount point like / (root), /home, swap (no format) etc.
Logical and primary does not apply to gpt partitioned drives which all new UEFI systems have. All logicals must be inside one extended partition. But only if formatting in advance with gparted do you see all those extra details.

Default installs are just / & swap, but if manually creating partitions you can add /home which is often suggested or many other partitions that often are only required for servers or advanced installs not average desktop installs.

My screen shot show me reusing an existing partition with an old install.

Okey. Hm but im not really sure yet what i am going to choose and so on. I press the +, cause there aint no other button to press, and in there i will do what? Sry but i just dont.  How much space? In what order, tex     2GB logical/primary? in ext4,  /root? /boot? 

WIth change? You mean i press Change, on the free space and then? 
So freaking much to keep up with.

---

### Post by oldfred on 2014-02-04
Since you have no partitions, you have to use + to create them. Only if already existing would you use change.

This shows the details also:
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)


My suggested sizes:
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by jabbe-duck on 2014-02-04
Yeah i did it ;) No problems here .D Dualbooting perfecly through grub ;) Works flawsless :D Thanks for all the answers

---

### Post by jabbe-duck on 2014-02-05
Hi again. SO i got it to work perfecly:) But now i installed GNOME3, but it didnt work as expected and now i cant change background and it hangs sometimes. and i think its best to just reinstall ubuntu. How do i do it now? 
Do i have to go back to windows again and partition ? Or can i just boot up a live usb and do as i did when i installed it first time??

---

### Post by Mark Phelps on 2014-02-05
I would be VERY careful about replacing an existing Linux install when there is a Windows install present on the same drive.  Lots of folks have been posting lately about doing a simple upgrade of Linux versions only to find their Windows partitions erased!

---

### Post by jabbe-duck on 2014-02-05
Okaj :/ ****. Hm how do i do then... ****. I have installed GNOME 3 but i dont disapears :/

---

### Post by oldfred on 2014-02-05
You can post a new thread on gnome issue. Most just install another gui.

But if re-installing do not use any auto options. Only use Something Else and select same / (root) as new root. Same if you have /home but do not reformat. It will find an existing swap automatically.

 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by jabbe-duck on 2014-02-07
> **oldfred said:**
> You can post a new thread on gnome issue. Most just install another gui.

But if re-installing do not use any auto options. Only use Something Else and select same / (root) as new root. Same if you have /home but do not reformat. It will find an existing swap automatically.

 Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)


Okey . I think i understand. Safest way is always to choose Something else, then you can choose by your own.

So im going to choose Something else / select the existint /root /home and the swap and then it should be safe not to wipe windows ? :D

---

### Post by oldfred on 2014-02-07
It should be safe, but anytime you do major system changes you want to have good backups. Mistakes happen. And important data should be backed up anyway as hard drives to fail.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Herman on 2014-02-07
I think I found an easy solution.

My wife has a laptop which came wih Windows 8 in it and even though she figured out how to use Windows 8 enough to do what she needed, she still wanted me to get rid of it and install Ubuntu for her instead. This is my first experience with Windows 8 and I wasted a lot of time reading all about EFI and Secure boot and other people's how-tos. Most of them were about how to dual boot, which is not what we wanted to do this time. We wanted to replace Windows 8 with Ubuntu. 
What I wasn't sure about was whether I had to do a lot of complicated stuff like making an extra 'boot' partition and switching things off in the EFI and stuff like that. I managed to find out how to make the darn thing shut down completely and I had a look at the settigns in the EFI, to go back to 'Legacy BIOS", but I can't remember if I left it like that or not, I think I left it in EFI mode. 

I had a spare 1000GB HDD lying around, brand new and still in the box, and I was getting impatient. All the reserach and complicated instructions I was reading was starting to drive me crazy.

Well I just swapped the original HDD with the brand new unformatted one and booted my 13.30 64-bit Ubuntu installation USB and it booted right up.
Then I ran the installer and just let it go with all the defaults, it was the easiest installation I have ever done in my life!
In no time at all the new Ubuntu installation was booting up and after placing the Windows 8 hard drive in an external USB3 case and doing a file rescue, and some updates and a little registering of accounts, I was able to present my wife with her new Ubuntu-only laptop. 

No special knowledge was required. I still don't know anything about Windows 8, secure boot or EFI.
The Ubuntu developers have done a great job, Ubuntu 13.10 is really nice and after all the FUD I was reading about Windows 8 it turned out to be a peice of cake to just replace Windows 8 with Ubuntu. 

The only trouble is, now we have an extra hard drive lying around with Windows 8 in it that's never going to be used for anything.

---

### Post by oldfred on 2014-02-07
@Herman
Another user posted that he regularly buys new laptops, better one's but with hard drive and like you, removes hard drive, installs SSD and Ubuntu for a very fast system. Then later when he sells it, he puts hard drive back in with unused Windows 8.
Did you use gpt partitioning? And BIOS or UEFI? 
Ubuntu works with gpt partitioning and will boot with BIOS or UEFI from gpt. Gpt has some advantages including a backup partition table. I now format all new drives with gpt and leave space for an efi partition at beginning, but boot with BIOS as that is all I have now.

---

### Post by Herman on 2014-02-07
@ oldfred,

I don't know what the installer did, I will need to examine the results. I  just let the installer have the entire disk and let it do its thing. I'll take a look and see what happened later and let you know.

Somebody else who also has a Windows 8 laptop approached me  yesterday to see if I can install Ubuntu for him, - my boss! So I have the  two most important people in my life wanting me to install Ubuntu for them. I can't afford for anything to go  wrong or my life could be made miserable for some time. 
Having the revomed  the entire Windows 8 and having it completely out of the equation makes  everything a lot simpler. It's worth a hundred bucks for a new hard disk  the peace of mind of knowing they can just switch hard disks again if  they ever want to.

---

### Post by jabbe-duck on 2014-02-10
Okey so im ready to install Xubuntu instead. But i know i will do as i did last time, one thing im unsure about thought, should i check over the box saying format on /root and home ? Or is it possible without format?:D

---

### Post by oldfred on 2014-02-10
Especially if you have any data in /home that you want to save you **do not** check format. Still best to have good backups of any of your data. If no data to save or right after another install you can check format.

I would normally check format for a new install for / (root), so it is clean. But sometimes to do a repair install you may want to not check it. Then all the system files and settings are refreshed, but some old data may be left, rarely would you want the old kernels or log files.

---

### Post by jabbe-duck on 2014-02-10
> **oldfred said:**
> Especially if you have any data in /home that you want to save you **do not** check format. Still best to have good backups of any of your data. If no data to save or right after another install you can check format.

I would normally check format for a new install for / (root), so it is clean. But sometimes to do a repair install you may want to not check it. Then all the system files and settings are refreshed, but some old data may be left, rarely would you want the old kernels or log files.


Okey :D 
Yeah i will probably format root and home then. IM just worried it will somehow erase my ntfs windows partitions.. I dont know why tought, if i do exactly as i did last time ;)

---

### Post by oldfred on 2014-02-10
The auto install does not always see Windows, and if it does not see it because it is hibernated or has other issues, then it may overinstall. Never had issues with manual install except the one time I selected the wrong partition to reformat. :)

---

