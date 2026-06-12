---
title: "Grub Rescue / Win7 Repair Disk"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by fantasticmuse on 2012-12-14
So, I decided to start from scratch and install uberstudent, or whatever the hell it was. Doesn't matter, cuz I didn't get that far.
 
I've done this before. I went in to device manager. I identified my recovery windows and linux partitions. I deleted my linux partition. Then I created a new partition. I set my new partition to format. Went ahead and started downloading my new OS iso. This entire process took several hours. Right at the end where everything had less than an hour left, I sat down and watched a movie with the fam.
 
Come back. Computers off. Turn it on.
error: no such partition.
grub rescue>
 
I whip out my handy dandy win7 repair disk. It loads up. It shows me the installation and where it is and I select it. I run the start up repair, and it fails. I go into the command prompt. It tells me there is no windows installed on any disk. I tried to go into system restore, figuring I have officially lost everything and have to go back to factory. Except my recovery disk isn't really my recovery disk, its my sister's and its not going to let me use it on my system. 
 
This makes absolutely no sense to me. Wth is happening and is there anything I can do to fix it????????????????

---

### Post by oldfred on 2012-12-14
The grub boot loader in the MBR had to find the rest of grub in the partition you deleted. You should just need to reinstall a Windows boot loaders. 

Make a Windows repairCD or flash drive or use a LinuxCD to install a Windows like boot loader.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

