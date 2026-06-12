---
title: "Another Windows 8 + UEFI Question"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by Enforcer5782 on 2013-02-02
I'm trying to install Ubuntu as a dual-boot with Windows 8 on an HP pavilion g6 (Windows 8 came pre-installed). I've been looking for several days on the web for help installing Ubuntu this way but nothing I've found on this forum or otherwise has been that much help.

This is not my computer and i CANNOT mess up Windows 8's functionality.

Can someone please provide a step-by-step guide for installing as a dualboot on a machine that came preloaded with W8. I've installed plenty of times before on W7 and blank machines, no problems.

---

### Post by oldfred on 2013-02-02
Welcome to the forums.

There are no guarantees. One user just erased Windows and wonders why his Windows will not now boot. Most install ok as with gpt partitions, you can easily add more.

Best to shrink Windows with Windows Disk Management. Then reboot a couple of times so Windows can run chkdsk or make other fixes due to the resize.

If you want to be safe, backup efi partition and Windows.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

            Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Not the same model but HP.
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
     
Some instructions for UEFI but Dell.
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

---

### Post by Enforcer5782 on 2013-02-02
So if I make a live USB of the 12.10 64-bit, disable quick boot, boot from USB and choose "Install alongside others" will that work? Why do I need to use disk management to shrink Windows and why on earth would I need to reboot multiple times after making just one change?

Btw, I don't see "Fast boot" in BIOS, is it at all certain the system has that? It's an AMD laptop.

---

### Post by oldfred on 2013-02-03
I thought you wanted to be on the safe side. Windows has to run chkdsk after every resize as it stores the partition start and size info in the partition boot sector and that has to match partition table. It sometimes want to make other corrections and chkdsk does not run all fixes on one pass. It may have to run more than once. 

Multiple uses have the fast boot setting, but it may vary by system. Some cannot get back into the UEFI menu with any key unless fast boot is off if Windows is not working. There is also a Windows 8 setting for quick boot and I do not even know if that is related, but turns off the hibernation.

---

### Post by Enforcer5782 on 2013-02-03
So what you're saying is, shrinking Windows using the Ubuntu installer to select partition size won't work.

I probably only need ~10GB of space for the Ubuntu partition so I'll try that as soon as I can get my hands on a blank DVD (UEFI on this laptop doesn't appear to recognize USB's). Would I be able to just run chkdsk from a command prompt to fix errors without needing to reboot repeatedly?

Also, on a side note: Any chance of a GPT-compatible Wubi release with 13.04?

---

### Post by oldfred on 2013-02-03
Most times you can resize Windows with Linux tools, but some just have errors and a few have errors that cannot be fixed. So it just is better to use Windows tools for Windows and Linux tools for Linux. (although sometime it seems we have to fix Windows from Linux).

When you run chkdsk from Windows it will tell you that you have to reboot for it to run.

---

