---
title: "Problem Win 8 dual boot Ubuntu 12.04 LTS"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by Rebootin on 2013-02-06
I am trying to install Ubuntu 12.04 on my wifes new HP Pavilion G7. The  computer came with Windoze 8 installed and I want to dual boot to  Ubuntu.

I used Win disk manager and shrunk the primary partition and added a 5 gig partition.
I then fiddled with the bios and **FINALLY** got the computer to boot from CD.
I then installed Ubuntu 12.04 desk. No problems.

When I rebooted, it booted to Windoze (no Ubuntu). I then used disk manager to look at the hard disk and found:

**0 Disk Basic 698.51 Gb**
1. Healthy (Recovery Partition) - 400 mb
2. Healthy (EFI System Partition) - 260 mb
3. (C:) Healthy (Boot, Page File, Crash Dump, Primary Partition) - 658.03 Gb NTFS
4. (F:) Healthy (Primary Partition) - 9.11 Gb RAW
5. Healthy (Primary Partition) - 5.89 Gb
6. Recovery (D:) Healthy (OEM Partition)

I thought you could only have 4 partitions on a disk ???
Where did Ubuntu go ???
Where do I go from here ??? I've read that Windoze is sensitive about messing with partitions.

In review, I realize I didn't format the new partition and I think that is part of the problem.

What should I do now to fix this ???

---

### Post by oldfred on 2013-02-06
Raw is a NTFS partition that partition table sees as NTFS, but PBR or partition boot sector has not been configured/formatted by Windows. PBR has more Windows boot code (even if not bootable) and the partition start and size. It is updated by chkdsk if size changes.

You cannot install Ubuntu into NTFS partitions except with wubi. But any Windows 8 pre-installed is UEFI with secure boot and uses gpt partitions. Wubi does not work with gpt partitions.

Also the 4 primary partition limit was MBR(msdos) partitioning. With gpt you now have a limit of 128 partitions with no extended nor logical partitions.
I would also suggest 25GB as a size for Ubuntu. If only 5GB you can just fit install into it but just about cannot run the updates as they need more space. Lots of housecleaning required and no room to really work.
Also good to have another shared NTFS data partition.

         You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Another HP somewhat different model which may make a difference.

 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

 UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

    HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by Rebootin on 2013-02-06
Thanks oldfred. Can I delete #4. *(F:) Healthy (Primary Partition) - 9.11 Gb RAW*, and #5. *Healthy (Primary Partition) - 5.89 Gb*, and #6. *Recovery (D:) Healthy (OEM Partition) - 24.84 Gb*?

I made a 6 DVD set of recovery DVDs before starting this project.

If so, where would the new 39.84 Gb go? Into a new partition?

Then I would have the space to install Ubuntu 12.10 64 bit.

As I said, the original install of 12.04LTS seemed to go fine but I can' find it on the HDD. What happened to it?

Thanks for all your help!

---

### Post by oldfred on 2013-02-06
Did you do a wubi install inside a NTFS partition. But wubi does not work with gpt.

Some of the new UEFI systems say not to delete the recover partition. With larger drives and gpt not having an issue with more partitions I would leave all the Windows partitions.

I would also make a full backup which is different than the DVD set you made.
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

    
If you want to see what is where post link to Boot-Info. You will need Boot-Repair to fix a bug in grub not creating correct chain load entries anyway.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Rebootin on 2013-02-06
Hey!

How about I reformat the entire drive and install Ubuntu 12.04LTS on a cleaned drive?

My wife would have a fit because she doesn't know Ubuntu, but I could give her my computer which is Win 7/Ubuntu 12.04LTS dual boot. That way she could have the safety net of Windoze.

I haven't used Windoze since I installed Ubuntu and I don't see ever going back to it.

Fresh installs should be pretty easy, right?

---

### Post by oldfred on 2013-02-07
You just want new computer? :) What will your spouse say about that?

I would never un-install Windows or any recovery partitions from a new UEFI system. Some vendor are having major issues and only work with those partitions existing. Plus you did pay for Windows.

 We get many users who rush into converting to Ubuntu and then find one game or program that only runs in Windows that they cannot live without. It took me 5 years to give up that one app myself.

Post link to BootInfo report.

---

### Post by Rebootin on 2013-02-07
> **oldfred said:**
> You just want new computer? :) What will your spouse say about that?

That's funny, that's _exactly_ what my spouse said. :D

I just discovered that Thunderbird and LibreOffice both have Windoze versions. So I'll install those for her and she can have her stupid Win 8 computer.

Thanks for all your help oldfred.

---

### Post by oldfred on 2013-02-07
I knew before I retired 6 years ago that I was converting to LInux. I only had Windows since that was what we used at work. So in Windows several years before I converted to Firefox, Thunderbird, OpenOffice & Picasa when it came out. First we dual booted as bookmarks & email was all in Windows. But I found I could move both Firefox & Thunderbird profiles to a shared Windows formatted partition and use the same profile in both Windows & Linux.  

I am still using those profiles in my shared NTFS data partition. I did not always update version at same time and profile still worked, but did try to keep in sync fairly soon.

---

