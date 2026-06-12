---
title: "Can't load windows7 after ubuntu but everything looks like it should."
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Quinten_ on 2015-04-25
[ATTACH=CONFIG]261521[/ATTACH][ATTACH=CONFIG]261522[/ATTACH][ATTACH=CONFIG]261523[/ATTACH]

Hi :)
My goal was to make my pc able to dual boot windows 7 and ubuntu desktop. I already had windows 7 installed on my pc so I followed a tutorial/guide. I already did this to my laptop(windows 8) also with UEFI and Grub Bootloader.
Ubuntu works! unfortunately it seems that it can't find windows anymore. 

[B]The Problem:
[/B]When I boot my pc I get grub comming up. Showing me:

Ubuntu 
Advanced options for ubuntu 
Windows Boot UEFI loader
Windows UEFI bootmgfw.efi
EfI/ubuntu/MokManager.efi
Windows Boot manager (on /dev/sda1)
system setup

All the windows options brings me to a black screen saying: Windows Error Recovery.
Here I have 2 options: 
Launch startup repair( Recommended)
Start windows normally

The repair load some files and bring me back to the same black screen and the start windows normally brings me back to the GRUB (maybe a restart not sure).
While ubuntu works fine I can't get windows working.

Changing bootorder to windows boot manager also doesn't change anything.
Also changing the bootmode to legacy & UEFI in stead of UEFI doesn't help.

In ubuntu I can check out my partitions ans still see all the files on them. Like C:/windows/system32/ for example.

I also checked out my GParted on my ssd
[see images above]

sda1: boot  
sda2: windows magic..
sda3: windows C: 
sda4: ubuntu 

Also ran boot repair multiple times:
[http://paste.ubuntu.com/10878248/](http://paste.ubuntu.com/10878248/)

Also did a recovery with my windows 7 cd but didn't do much.

Grub update, check.

When I choose Windows Boot UEFI loader I now get this:
error file EFI/Boot/bkpbootx64.efi not found
this was after I used boot-repair and checked to rebuild the MBR.

[B]Basic Specs
[/B]Processor: intel i5
Ram: 8GB 
Graphics: 2 x GTX 560 TI 

OS: windows 7 64 bit 

SSD: samsung evo 240 gb 
HDD: 1 TB 

I use the SSD for windows main files and the HDD for some data.
Went to do the same for ubuntu.

**Let's install ubuntu:**

1. Create partitions
Created 2 (total of 4) partitions by shrinking the windows ones inside windows.
One on the SSD (20 GB ) and one on the HDD (50 GB).

2. Ubuntu ISO 
Downloaded the latest ubuntu version 64 bit burned it to an USB.

3. Installing ubuntu 
Installed Ubuntu inside the live demo. Setting the root to my SSD partition and my home to my HDD.

Everything worked, but when I tried to boot windows.......


I really appreciate any help you can provide.

Thank you in advance,

- Quinten

---

### Post by sgian on 2015-04-25
I suspect that when you resized the partition, something essential for windows got deleted.  Hopefully someone more skilled with windows can help you, otherwise my solution whenever this happened to me has been to reinstall windows (or not to reinstall windows since I rarely use it lol).  Next time before installing any second OS, defragment the windows installation.  That seems to work for me in preventing this problem from happening.

---

### Post by Quinten_ on 2015-04-27
Thanks for the reply sgian!

I also think it might be the data loss when shrinking unfortunately I really want windows back for some school applications and like all of my games ;(

So okay just reinstall windows.... but hey now I got a 0xc0000225 error and no possible way to get to the CD repair tool from windows working and the boot-repair with multple settings also doesn't work...

*sigh "Just try dual-boot,easy" they said..

---

### Post by oldfred on 2015-04-27
You have to shrink Windows from inside Windows using its tools and reboot immediately so it can run chkdsk. It may need that chkdsk which you can only run from Windows repair console. Either your install, if you can directly boot from UEFI (not grub menU) or from a Windows repairCD or installer DVD.

Since drive is gpt, you have to boot Windows installer in UEFI mode not BIOS mode to reinstall. 
Both Windows & Ubuntu install in boot mode that you boot flash drive installer. Or either UEFI or BIOS/CSM/Legacy.
Grub only boots working Windows, so you have to have a way to boot into a Windows repair console if Windows has issues. You should have that even if not dual booting.
       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

Since UEFI version of Windows 7, repair flash drive must be more like the Windows 8 version.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

