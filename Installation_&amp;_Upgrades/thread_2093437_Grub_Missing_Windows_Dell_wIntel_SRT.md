---
title: "Grub Missing Windows Dell w/Intel SRT"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by hnsilva on 2012-12-10
:confused:Hi, my name is Hernandes.

Please analyse [http://paste.ubuntu.com/1423413/](http://paste.ubuntu.com/1423413/) and help me to set my Grub2 let me choice Windows or Ubuntu to boot. Currently only load Ubuntu.

I was trying follow the instructions of the topics below to setting dual boot on my Dell Vostro 3560 with mSSD 32GB cache Intel Smart Response:

-http://ubuntuforums.org/showthread.php?t=2077149
Intel SRT - Dell XPS
-http://ubuntuforums.org/showthread.php?t=2038121
-http://ubuntuforums.org/showthread.php?t=2036204
-http://ubuntuforums.org/showthread.php?t=2020155
Some info on re-instating 
-http://ubuntuforums.org/showthread.php?t=2038121
-http://ubuntuforums.org/showthread.php?t=2070491

---

### Post by oldfred on 2012-12-10
Welcome to the forums.

I moved you to your own thread from Yann's thread which is getting too busy. Also better as then if/when solved you can post solved and others may find thread when searching.

[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)

Not sure where you are at on Intel SRT issues. But you are missing the Windows boot files.
Windows 7 installs to two partitions, a 100MB boot/repair partition and the main or c: drive. You are missing the two boot files from the boot partition.

       Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 


You can have first two boot files in main partition but have to put boot flag on sda3 for Windows to repair it with gparted or make active from Windows and use a Windows repairCD to fix it.


       
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by hnsilva on 2012-12-11
Hi Oldfred!

My Win 7 boot partition is located in /dev/sdb, that is a 32GB mSSD for cache (Intel SRT), and GRUB2 don't is seeing this partition and files. I tried fix this with boot-repair unsuccessfully.

#-o Let me explain how this occurred.

I was following the instructions contained in these threads:

- [http://ubuntuforums.org/showthread.php?t=2077149](http://ubuntuforums.org/showthread.php?t=2077149)
Intel SRT - Dell XPS
- [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
- [http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
- [http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
- [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
- [http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

My intention was install Ubuntu keeping the Intel SRT works.

I will describe to you, step by step of that i did to install Ubuntu:

1) I Disabled Acceleration from Intel RST in my Windows System;
2) on BIOS I changed RAID to AHCI;
3) I used the live CD to boot into ubuntu and used Gparted to shrink Windows partition and create the partitions for install Ubuntu;[ATTACH]228541[/ATTACH]
4)I ran the comands "sudo dmraid -E -r /dev/sda (Return messages no RAID detecteds, something similar)" and "sudo dmraid -E -r /dev/sdb (Return advises for deleting metadata, I confirmed with yes)";
5) Installed Ubuntu 12.04 normally on /dev/sda1;
6) Finished instalation, so then, my laptop only loads Ubuntu. Grub2 don't appear. Ran boot-repair, Grub2 appear but only see Ubuntu.

From now on, I am grateful to be helping me!

Thanks a lot!!!

PS.: ;)Sorry for my english that is very bad!

---

### Post by oldfred on 2012-12-11
You English is fine. :) 

A user added some comments on Intel SRT. Not sure if all true but looks useful in general.
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Your install process seemed fine. I do not have Intel SRT, but have followed the threads.

But you are missing the Windows boot partition. Often sda1, or if Vendor puts his recovery partition first, them it is sda2 and is only 100MB. But beside the two boot files I also has the Windows recovery tools (or Windows repair console). So you cannot press f8 to fix Windows. You have to have a repairCD or USB. 

If you did not make one before, do you have another computer with Windows or know someone with the same 32 or 64 bit version? Work, school, neighbour?

The repair console used to be a free download, then Microsoft made them charge & it became $10 and I just looked and now it is $20!!! I guess Microsoft does not want to let a user fix his system.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

And be sure to move boot flag or from Windows use the make active to make the main Windows install the boot partition or active partition as it only will repair the boot partition.

---

### Post by hnsilva on 2012-12-11
> Often sda1, or if Vendor puts his recovery partition first, them it is sda2 and is only 100MB. 
I deleted both when used Gparted.:lolflag:
> you are missing the Windows boot partition.
Now, i'm using Gparted to liberate 200MB before /dev/sda3, so then i will rebuild Win boot partition.

> A user added some comments on Intel SRT. Not sure if all true but looks useful in general.
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

Reading.

---

### Post by oldfred on 2012-12-11
I know you do not have to have the separate 100MB partition with regular Windows 7, not sure if Intel SRT makes any difference. Early installs of 7 were over Vista which did not have separate boot partition. The reasons for the separate boot partition were so you could encrypt the main install as boot could not be encrypted and to have repair console possibly accessible with f8 if main install needed repairs.

You can put boot files in main install and just have a separate CD or flash with a repair console. And you probably should have separate repairCD anyway.

---

### Post by hnsilva on 2012-12-11
Man,

It's working perfectly now!!! Tomorow I will detail the process to anyone who needs and mark this thread SOLVED.

Now I'm finishing the configurations of the programs that i use and moving the files of the my old laptop.

Thanks for help me.:D:D:D:D

---

### Post by oldfred on 2012-12-11
Glad you got it working.

I like to document my system boot configuration with bootinfoscript. The script is not as complete as the BootInfo report but I can run script as part of my rsync backup, so I always have a current copy somewhere.

---

### Post by verzx on 2012-12-11
Maybe you should try using the Windows 7 disc and start up repair, or use the Start up repair on Ubuntu. Maybe that will fix it. :)

Look at this: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hnsilva on 2012-12-12
Hi Oldfred!

Finally I finish the configuration of my new laptop.

Between yesterday and today, I had to answer some unfinished requests, and because of this, I delayed to coming back in the forum.

> I know you do not have to have the separate 100MB partition with regular Windows 7, not sure if Intel SRT makes any difference. Early installs of 7 were over Vista which did not have separate boot partition. The reasons for the separate boot partition were so you could encrypt the main install as boot could not be encrypted and to have repair console possibly accessible with f8 if main install needed repairs.

You can put boot files in main install and just have a separate CD or flash with a repair console. And you probably should have separate repairCD anyway.

After i read your message above, i decided put boot files in main install, but this yet don't solved my problem. I ran boot-repair desperately trying to fix the boot and did not work.

I had to run boot-repair in advanced mode, so then, i marked the option to delete/clean/purge the current Grub installation before reinstalling. During the reinstall i was asked for the local to install, then I selected to install in both devices, /dev/sda and /dev/sdb.

After that, my Win 7 partition returned to load and I have reactivated the acceleration Intel RST.

One more time, Thanks a lot and sorry for my bad english.

PS.: For use the boot-repair need the live CD. To enable install Grub on SSD, Ubuntu must have the "mdadm" package installed "sudo apt-get install mdadm". 
In [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121) have the instructions to re-enable Intel RST acceleration.

):P Until next time!!! \\:D/\\:D/

---

