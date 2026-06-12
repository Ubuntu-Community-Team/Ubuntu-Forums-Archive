---
title: "Installing ubuntu 12.04 lts with windows 7 dual boot, please check what is wrong here"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by testbear on 2012-11-10
Hi,
I am a fan of UBUNTU and really wanted to use it on my new sony vaio laptop.
I have been using UBUNTu 12.04 lts on my computer, and I have no problems in it, or when ever I have had any problem, it got fixed just by searching and implementing.

I have recently brought a sony vaio laptop
configuration is
Sony E series- VPCEB44EN
Intel core i3-380 M processor 2.53 GHz
wIndows 7 home basic 64 bit
ram 3gb

Now I have been having this weird issues.
The laptop shuts down automatically, sometimes, just after restarting and sometimes after I have booted in ubuntu

When I installed ubuntu, I could not see the dual boot option , so I installed boot repair and it got fixed.

Now on the startup screen, I have these options
see the screenshot

it is showing two windows 7 
as in the screenshot

the hard disk is of 320 gb
in windows, I can see, 210 gb of space
in ubuntu I can only see 33 gb of space

please, let me resolve this issue and if I posted it in wrong section, kindly move it to appropriate section, and help me resolve it

I am a complete novice and hence require some help here to set it right.

---

### Post by 2F4U on 2012-11-10
Two possible reasons come immediately to my mind:
1. Overheating. Can you check the temperatures in Ubuntu?
2. Bad RAM. Can you run memtest for at least two iterations?

To further diagnose the problem you should take a look into the system log file (/var/log/syslog) directly after such a shutdown and look for any unusual errors.

---

### Post by oldfred on 2012-11-10
Windows normal install is a (hidden) 100MB boot/repair partition and the main install. But you can directly boot a main install if boot files are in that drive. Windows keeps it separate so you can encrypt your main install if desired. Also you may be able to get into repair console if main install is corrupted, but if boot is corrupted then you cannot get into main install.

Boot Repair copies boot files from boot partition into main install. Then you can boot either. Either way you still should have a separate CD with the Windows repair tools in case you cannot boot.

If you do not want both entries you can use Grub Customizer to hide one.

New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by testbear on 2012-11-11
> **2F4U said:**
> Two possible reasons come immediately to my mind:
1. Overheating. Can you check the temperatures in Ubuntu?
2. Bad RAM. Can you run memtest for at least two iterations?

To further diagnose the problem you should take a look into the system log file (/var/log/syslog) directly after such a shutdown and look for any unusual errors.


How do I check the temperatures and run memtest for two iterations?

---

### Post by testbear on 2012-11-11
> **oldfred said:**
> Windows normal install is a (hidden) 100MB boot/repair partition and the main install. But you can directly boot a main install if boot files are in that drive. Windows keeps it separate so you can encrypt your main install if desired. Also you may be able to get into repair console if main install is corrupted, but if boot is corrupted then you cannot get into main install.

Boot Repair copies boot files from boot partition into main install. Then you can boot either. Either way you still should have a separate CD with the Windows repair tools in case you cannot boot.

If you do not want both entries you can use Grub Customizer to hide one.

New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

I get it why to use grub customizer.
why create windows repair cd?

---

### Post by darkod on 2012-11-11
> **testbear said:**
> I get it why to use grub customizer.
why create windows repair cd?

Because most branded machine these days don't come with windows install media, only a recovery partition which is mostly useless. Usually it's recommended to make the win7 rescue cd so that you have a cd that can repair the windows bootloader if needed one day, or run basic checks like chkdsk, etc.
Of course, this media can't serve to make a new windows install, only to do some basic rescue operations.

---

