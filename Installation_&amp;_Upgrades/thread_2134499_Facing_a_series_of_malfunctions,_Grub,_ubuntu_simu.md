---
title: "Facing a series of malfunctions, Grub, ubuntu simultaneously"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by patghosh on 2013-04-11
Hi All

Please pardon my level of (in)competence in all matters Ubuntu.
I am facing a sequence of problems, which for clarity's sake I shall put down in the chronological order.
I had a dual boot set up with Ubuntu 12.04 and Windows 7. Suddenly I couldn't log in to Windows 7. It showed the option in grub (still does), but selecting it just changed the screen color for a few seconds and grub menu just reappeared.

I saw posts mentioning purging the grub, and tried doing it but it seems that after purging grub didn't reinstall and I was logged out with Grub Rescue screen.

Going through the forums, I came across the post on boot repair. I downloaded 'secure', created a usb from the iso file and tried boot repair but that didn't work. 
I thought going for the upgrade to 12.10 might solve the problem but my usb stopped midway creating some sort of an unholy mess because even though I can see my grub menu it just mentions ubuntu (and not the usual long line containing words like pae, generic ). Prior to this ubuntu secure detected 12.04 and gave the option for upgrading.

Now it just says mutliple OS are present with options like installing alongside and deleting disk for installation.

I would obviously like to go back to yesterday (both OS working with my data), that would be sort of my goal but I am not sure how to go about getting out of this mess.

---

### Post by oldfred on 2013-04-12
I am not sure where you are at now. The Windows issue was Windows and probably just needed Windows repairs. All grub does is chainload to Windows and then Windows does its thing. So any changes to grub or Ubuntu will not help Windows. Only very minor fixes to Windows can be done from Linux. Do you have a Windows RepairCD or flash drive?

But now you have upgraded, which may have other issues with grub or Ubuntu?? Do you get grub menu? Does Ubuntu boot?

Best to post link to BootInfo report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

