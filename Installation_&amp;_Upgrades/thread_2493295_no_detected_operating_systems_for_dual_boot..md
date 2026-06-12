---
title: "no detected operating systems for dual boot."
date: 2023-12-09
forum: Installation &amp; Upgrades
---

### Post by paulberry on 2023-12-09
Good evening.  This is yet another..........

I want to dual boot Win 10 Pro, and Ubuntu, but the 22.04.3 LTS does not detect the Windows 10 installation.

I am new to Ubuntu/Linux.  Both the LTS and the new version seem to run fine from the USB ("try" mode).


Dell Precision T7910 workstation (1998)
Windows 10 Pro
2 processors
1TB SSD (no HDD)
1TB RAM

Some things I tried/checked....

Created another partition for Ubuntu via Windows to begin the manual partition process,
but I had no confidence that it would dual-boot, or that Windows would not be damaged.
(also had to disable Windows page file so I could get space from the primary partition)

RAID disabled
Secure boot disabled
Set to AHCP disk mode
Fast boot disabled
Hibernation disabled (Searched for hiberfil.* and none exists).
I do not have Optane
I enabled the system and admin passwords, and I did not notice additional relevant options made available.  
The partition type is not listed as "dynamic".  Is NTFS.


What I was unable to comply with, or what seemed odd...

"If the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-UEFI) mode,
 then you must install Ubuntu in Legacy mode too."
Windows is set to legacy BIOS boot.  But I cannot boot legacy from the installation Sandisk USB thumb drive.
Selecting "USB Storage Device" under legacy boot fails to recognize the thumb drive.
However the Sandisk boots fine with UEFI.
I tried switching Windows to UEFI, and it would not boot.
So I could not get both OS to boot in the same mode (BIOS or UEFI).

The LTS version could not detect Windows. but the 23.10 (with updated installer) did detect it.
But 23.10 could not be used, because it crashes before completing the install.
So the newer Ubuntu version is able to detect the Windows partition.

Did I miss anything?  Next steps?

---

### Post by tea for one on 2023-12-10
Probably not the reply you wish to read, but..........
Have you considered backing up your Windows data and installing Windows 10 in UEFI mode with GPT?

---

### Post by yancek on 2023-12-10
How old is the Dell computer you are using?  Was windows 10 preinstalled on this machine?  Is the drive you are using GPT?  If it is GPT, microsoft requires windows to be installed in UEFI mode.  If you don't know whether you have a GPT disk, you can get that information from the live installer by going to a terminal and entering the  command:  sudo parted -l

No point in creating a partition for Linux from windows as you will need to format the partition with a Linux filesystem and you cannot do that with a default windows.  The better option is to use Disk Management in windows and shrink the largest partition to create unallocated space on which to create partitions for Linux.

What 'system and admin passwords' are you referring to?

If you are installing a Linux system on the same hard drive on which you have windows, you should install them both in the same mode.  If you have an EFI system, you should be able to select either from the BIOS firmware Boot Options on boot.  If you have a Legacy system, boot code needs to be in the MBR and that code can only be from one system and it is best to be the Grub bootloader as it easily will chainload to boot a windows install.

> The partition type is not listed as "dynamic".  Is NTFS.

I'm not sure what you are referring to with the above comment.  The term 'dyanmic' is something that is only used on windows.  If you are trying to install Ubuntu to an ntfs filesystem, stop now.  It will not work.

If your Dell is not more than 10 years old and had windows installed from the factory, it is almost surely an EFI install.

---

### Post by paulberry on 2023-12-10
The more I dig into it, the more it looks like that is what I will have to do.  Microsoft is supposed to have a utility that converts without data loss (at your own risk), called MBR2GPT.
Also, from browsing their forums, there is some indication that the SanDisk may have an issue with booting legacy and maybe another brand would work.  Maybe will investigate that, maybe not.

Thanks for the reply.

---

### Post by tea for one on 2023-12-10
Sandisk usb devices will boot Ubuntu in both Legacy and UEFI modes.
It depends on which software you used to create the usb.
Please see attachment.

Your PC can also support multiple disks.
You may want to add another disk dedicated to Ubuntu.
Windows and Ubuntu on separate disks (UEFI/GPT each with an ESP) is preferable to dual-booting on one disk.

Nevertheless, I strongly recommend that you start by backing up your Windows 10 data and re-installing in UEFI mode with GPT.
If you have a backup, then it may be worth trying the Microsoft conversion tool.

---

### Post by paulberry on 2023-12-10
> **yancek said:**
> How old is the Dell computer you are using?  Was windows 10 preinstalled on this machine?  Is the drive you are using GPT?  If it is GPT, microsoft requires windows to be installed in UEFI mode.  If you don't know whether you have a GPT disk, you can get that information from the live installer by going to a terminal and entering the  command:  sudo parted -l
**Parted reports the SanDisk as "GPT", and the SSD as "msdos".  Sounds pretty legacy to me.**

No point in creating a partition for Linux from windows as you will need to format the partition with a Linux filesystem and you cannot do that with a default windows.  The better option is to use Disk Management in windows and shrink the largest partition to create unallocated space on which to create partitions for Linux.
**Ok, I'll either shrink it in Windows, or use the installer function, which I think does that.  I'm still not sure if creating a separate partition will break the dual boot function, or if that is a critical piece of dual-boot.  Probably the latter.**

What 'system and admin passwords' are you referring to?
**Some other post on this topic suggested that some BIOS options (that I need to enable/disable) might not be visible until the BIOS security features are enabled.  I didn't notice any difference, but there are many switches,and I didn't screen shot before and after to compare.  Just didn't find the specific options mentioned.**

If you are installing a Linux system on the same hard drive on which you have windows, you should install them both in the same mode.  If you have an EFI system, you should be able to select either from the BIOS firmware Boot Options on boot.  If you have a Legacy system, boot code needs to be in the MBR and that code can only be from one system and it is best to be the Grub bootloader as it easily will chainload to boot a windows install.[B]
Grub can go on my current Win install?  I'm going to try converting the msdos to GPT first.  If that doesn't work out, I'll try to decipher what you're telling me here.  I'm still wet behind the ears with Linux.[/B]

I'm not sure what you are referring to with the above comment.  The term 'dyanmic' is something that is only used on windows.  If you are trying to install Ubuntu to an ntfs filesystem, stop now.  It will not work.
**Like most of what I tried, it was based on suggestions from posts regarding a similar issue of no OS detected.  Could have also been a youtube video.  Both the source, and my interpretation are questionable.  He said to make sure it is not dynamic.  I don't recall the specifics, but just posted it as something I did, in case it was important.**

If your Dell is not more than 10 years old and had windows installed from the factory, it is almost surely an EFI install.
**It probably was EFI originally in 1998, but not after the Ebay refurbisher did his magic.  Even so, it surprises me a bit that this is a bump in the road to installation, since one of the selling points of Linux is that it works on older hardware.  It seems to me that either a legacy boot ISO image should be available, or at least the GPT requirement be more of a 'front-page' item for the benefit of near complete Linux ignorants like myself.**

**Thank you for the response.  The journey continues, and I'll post what eventually worked.**

---

### Post by paulberry on 2023-12-10
I used balenaEtcher as suggested in an installation instruction.  I try the legacy USB option (which does not explicitly say "Sandisk", as the UEFI option does), and the boot just immediately fails.

Another disk? Maybe.  Right now I'm suffering from "I've already purchased too much hardware" syndrome.  That should subside in a few days.

As far as a backup, I really don't have anything on the Windows installation that can't die.  I've only had the system for a week or two, and much of that was trying to install Ubuntu.  It's just the OS, which I'm told can be downloaded.  Am I too casual about this?

I think it's time to step back and mull over my options.

Thanks

---

### Post by tea for one on 2023-12-10
> **paulberry said:**
> I used balenaEtcher as suggested in an installation instruction.
Have a look at [https://www.ventoy.net/en/doc_start.html](https://www.ventoy.net/en/doc_start.html)
> **paulberry said:**
> Another disk? Maybe.  Right now I'm suffering from "I've already purchased too much hardware" syndrome.  That should subside in a few days.
Yes, I've suffered the same torment, but it usually dissipates after a good night's sleep (or a large glass of Malbec) ;)
> **paulberry said:**
> As far as a backup, I really don't have anything on the Windows installation that can't die.  I've only had the system for a week or two, and much of that was trying to install Ubuntu.  It's just the OS, which I'm told can be downloaded.
You can download Windows 11 without effort [https://www.microsoft.com/software-download/windows11](https://www.microsoft.com/software-download/windows11)
Don't forget your product key
> **paulberry said:**
>  Am I too casual about this?
It's the Malbec
> **paulberry said:**
> I think it's time to step back and mull over my options
Malbec and mulling are best mates - they begin with the same letter

---

### Post by paulberry on 2023-12-11
I appreciate the advice, but I'm afraid that all I will accomplish with Malbec is an additional nap.

Ventoy is a nice utility.  Once the flash drive was set up as MBR, the legacy USB boot option functioned and I was able to install Ubuntu.  I guess now would be the time to convert the drive to GPT, since there's no data, but I don't see a compelling reason.

The  only remaining issue is that I get an "Invalid Partition Table!" error on boot,  but I hit <enter> and it progresses to the GRUB boot menu.  Both  the Windows 10, and Ubuntu options function.  I can live with the error message.

In a nutshell, my SSD should have been GPT and most or all of this drama would have been avoided.  The solution I chose was to downgrade the flash drive to MBR so they matched.  Upgrading the SSD to GPT might have been more correct, but this was good enough.  Maybe I'll do that later.

It might be nice to have the install program compare the boot methods for the drives and give a warning, instead of somewhat mysteriously failing.

Thanks for all the support!

---

