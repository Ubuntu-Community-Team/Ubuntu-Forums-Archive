---
title: "Ubuntu on existing Windows machine"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by peter228 on 2016-05-21
I have been asked to install Ubuntu on a laptop.   Windows 8.1 is already installed.

The wish is to move Windows to a virtual machine and have Ubuntu as the main operating system on the laptop.

I have no experience with Windows and so ask if there are any suggestions of the procedure?   

My idea at present is to make Windows install media from the present install and then overwrite the system with the Ubuntu install, set up a VM and reinstall Windows from the install media.  However, I recall that it is possible to install Ubuntu alongside Windows.  Not sure what boot loader that would use but that approach may be a stepping stone. Perhaps there are other options to consider.

So I really would be interested to hear of any suggestions....

---

### Post by ubfan1 on 2016-05-21
Read 
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
A dual boot system is far easier than the plan you outlined.

---

### Post by RobGoss on 2016-05-21
Hello and welcome to the forum, I would suggest a dual boot if that's what you want. Installing Ubuntu as a dual boot is fairly simple. Mentioned in post #2 they recommend doing your homework because if this is a new machine then it's most likely you will have to deal with **UEFI** and** Legacy **

One thing to remember is when you install Ubuntu make sure what ever boot order Windows is in you'll need to install Ubuntu in as well. Here's a great tutorial that will help you in the process [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2016-05-21
I did not think it was legally possible to install an existing Windows into a VM, It has to be a new install with a new license.

Some more info on UEFI & dual boot.
Best to use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk. Do not use Windows to create partitions.
Make sure fast start up in Windows is off.

       [URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html
[/URL]

These links and more info are in link in my signature below.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by RobGoss on 2016-05-21
> **oldfred said:**
> I did not think it was legally possible to install an existing Windows into a VM, It has to be a new install with a new license.

Some more info on UEFI & dual boot.
Best to use Windows to shrink the NTFS partition and reboot immediately so it can run chkdsk. Do not use Windows to create partitions.
Make sure fast start up in Windows is off.

       [URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html
[/URL]

These links and more info are in link in my signature below.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

You are correct Fred it will need to be install on the original registered machine  with a licensed copy of Windows 10

---

### Post by peter228 on 2016-05-22
Well this is fun.  Thank you to everyone who has added to this thread.

There are so many links for me to read now that this is going to take a while to do the homework.

I had thought about installing along side since this is an offered option from the Ubuntu installer but I would like to see some distance from Windows.  If Windows gets trashed (which apparently is very likely - from reading other forums) then it is possible that the boot loader gets trashed as well. If that is the Windows boot loader then Ubuntu would be trashed as well.  Yes, a new boot loader could be installed but that is only if you have a memory stick ready and know what to do and in this case neither will be likely resources.

So I need to look more carefully at the hardware, read up more on UEFI and think about dual boot.    Dual boot really is not good though ... if you are to use an operating system then use it by default.  If a university requires Windows to be used for homework assignments then use it but a VM would be perfect for this ...

---

### Post by oldfred on 2016-05-22
Windows usually does not get trashed, but users select the full drive install option either not understanding in Linux a drive is the entire physical drive or just making wrong install choices. That is why we always suggest full backups.
But drives do fail, and the vendor recovery or Windows recovery on the same drive will not help when drive fails and you want to use a new hard drive or SSD. So best to make the full backup of Windows.

I did get a new Dell SFF system for just TV use. I had not planned on using the Windows 8 but fortunately keep it as Comcast only worked with Windows.
But I made the Dell backup, the Windows backup & a full image backup with Macrium Reflect. Multiple flash drives & DVDs were required.

---

