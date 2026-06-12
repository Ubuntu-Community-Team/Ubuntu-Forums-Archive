---
title: "Installation wubi Sony VAIO SV-E14A3M6E"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by Sebastian_Ulloa on 2014-02-23
Hey everybody,
I tried to install ubuntu in my win7 and I have the problem of the missing wubildr.mbr that goes like this:[INDENT]
[/INDENT]
Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

 1. Insert your Windows Installation disc and restart your computer. (Windows came preinstalled).
 2. Choose your language settings, and then click "Next."
 3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.  

File:\Ubuntu\winboot\wubildr.mbr
status: 0xc0000098
Info: The application or operating system couldn't be loaded because a required file is missing or contains errors.

I haver just tried like everything, first the boot-repair with a LiveCD; also I tried to change the BIOS, I changed the UEFI boot to the Legacy boot and it was even worse because after that I got the message "Not Operating System Found...".
Also I looked for the fast boot and the secure boot option in the BIOS but I didn't find it.
Finally I tried to install Ubuntu 13.10 with a pendrive but in the installation it doesn't show me the that Win7 is installed.
 I think that the only option that I have is to install it with the pendrive and hope my Win7 not get lost.
So if someone knows another way to repair it or an excellent tutorial for doing this I will be very greatful!

---

### Post by oldfred on 2014-02-23
If you have one of the few Windows 7 systems that is UEFI, then you have gpt partitioning. And wubi does not work with gpt partitioning. Many say it does not work with Windows 8, but that is because all new Windows 8 systems that are pre-installed use UEFI with gpt partitioning.

If Windows is UEFI, then you will not be able to boot in BIOS mode.
Windows only boots from gpt partitioned drives with UEFI.
Both Windows on Ubuntu only boot from MBR(msdos) partitioned drives with BIOS mode.

You may need Windows repairs and Boot-Repair can only do minor Windows fixes. Most Windows repairs need a Windows repairCD or Flash drive.

Best to see details:
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Sebastian_Ulloa on 2014-02-23
I know that if I use the windows repair cd I have to put some commands in the prompt, do you know the full steps?

---

### Post by oldfred on 2014-02-23
I only know the Windows BIOS versions. Not sure if UEFI is the same or not. But you must boot repair flash drive in correct mode, either UEFI or BIOS to match your install.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 Repair install
[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)
f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

   Older - oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by Sebastian_Ulloa on 2014-02-23
Thanks a lot, I'm going to try it

---

