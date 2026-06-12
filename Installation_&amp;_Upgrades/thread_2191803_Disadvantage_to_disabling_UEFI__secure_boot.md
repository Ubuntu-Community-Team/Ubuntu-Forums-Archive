---
title: "Disadvantage to disabling UEFI / secure boot"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by p.nieters on 2013-12-04
Hey,

I'm going to install ubuntu on my new win8 dell laptop and it seems quite a hassel to deal with UEFI/secure boot.
So, why not disable it? I do not need win8 on the machine in the first place, so are there any more disadvantages, or would you say
I can just go ahead to the legacy boot priority settings in my bios and not worry too much?

---

### Post by fantab on 2013-12-04
Yes you can disable EFI, and 'Secureboot'.
 

Why you shouldn't?
While 'secureboot' is Windows 8 "security" feature, UEFI is OS independent. It IS the new BIOS.
UEFI is a replacement for BIOS. Simply put, UEFI interacts better with newer hardware. (Not that BIOS doesn't, but it was getting old for the newer hardware technologies out there). 
Windows can only communicate with UEFI when its booting from GUID Partition table (GPT), which by the way is a must for UEFI. GPT is, again, a better option that older 'msdos/MBR'. 
Windows can only boot in UEFI with GPT, while ubuntu can boot in both _BIOS/Legacy and UEFI mode. _

I'd say install Ubuntu with UEFI enabled.

Read through the linked info.
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
[https://wiki.archlinux.org/index.php/GUID_Partition_Tabl]("https://wiki.archlinux.org/index.php/GUID_Partition_Table")

About 'Secure boot':
[http://technet.microsoft.com/en-us/library/hh824987.aspx](http://technet.microsoft.com/en-us/library/hh824987.aspx)

---

### Post by p.nieters on 2013-12-04
Alright, I will keep reading then, choosing the better solution and learn something =)

From what I ve gathered so far, it might be the best solution to USB install ubuntu via the classical method and then
"patch" the system afterwards to work with the UEFI standard - is this the route I should go down?
From the top of my head, I could also install from within windows. Might this be easier? Can I get rid of windows easily after?
Also, did I in fact understood what I was reading? =)

Installing from USB would also allow me to check if networking, audio drivers and the trackpad work just fine,
my last worry however is, that disabling UEFI floods me with warnings which left me a little wary. Can I just reenable it and
boot to windows if all goes to sh*t?

Thanks a bunch! =)

---

### Post by oldfred on 2013-12-04
Currently I do not see a lot of advantage to secure boot. Later when it all if improved it may be worth having. No BIOS based system has secure boot as an option anyway.

 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

You cannot install wubi or the version that works inside Windows with any pre-installed Windows 8 systems as wubi does not work with gpt partitioning. If not wanting to repartition and wanting just to try Ubuntu you can use flash drive with persistence which lets you save some info or if a larger flash drive even a full install. Not as fast as full install to hard drive but can be functional as a test system.

The newest Ubuntu installs to standard UEFI systems reasonably well if you do a few things up front. Ultrabooks with Intel SRT and RAID and dual video add complications, but those would also exist with any install UEFI or BIOS.

While you can do a BIOS install and use Boot-Repair to convert to UEFI, that is more for the few systems that only boot Windows and will not boot anything else except in BIOS mode. Boot-Repair then can uninstall grub-pc(BIOS) and install grub-efi(UEFI) and do a 'buggy' UEFI fix to rename grub's boot file to have the Windows efi file name so UEFI will still boot Windows but actually boot grub/Ubuntu. Then from grub you can boot the renamed Windows efi file. Later Windows updates may then cause issues as it will update the Windows file, but that really is grub so further repairs would be required. 
Or best not to install in BIOS mode and best to confirm if you can boot ubuntu entry from UEFI menu and not run the buggy UEFI update from Boot-Repair.

Some of the very newest systems need all the UEFI updates in 13.10. They will be in 12.04.4 but are not in current 12.04.3.

Lots of info on installing in link in my signature.

---

### Post by fantab on 2013-12-04
> **p.nieters said:**
> 
From what I ve gathered so far, it might be the best solution to USB install ubuntu via the classical method and then
"patch" the system afterwards to work with the UEFI standard - is this the route I should go down?
From the top of my head, I could also install from within windows. Might this be easier? Can I get rid of windows easily after?
Also, did I in fact understood what I was reading? =)

Installing from USB would also allow me to check if networking, audio drivers and the trackpad work just fine,
my last worry however is, that disabling UEFI floods me with warnings which left me a little wary. Can I just reenable it and
boot to windows if all goes to sh*t?


You don't knowingly and on purpose make a mistake then fix it later. Doesn't sound right, does it?
Either go with UEFI 'disabled' or with UEFI 'enabled'.
Installing Ubuntu with UEFI is simple, we just have to take care of certain preconditions depending on your 'computer hardware and UEFI version and its implementation'.
No new laptop/destop is being made with BIOS, its all UEFI. For now, we can use Legacy/BIOS mode as an option but we can't forever.

Trying to install UBUNTU within Windows with WUBI is a horrible idea, especially with UEFI and Windows8 in the picture.

Using either Ubuntu DVD and/or USB you can "Try Ubuntu without installing" and check how it fares on your Hardware.

Yes you can 're-enable' UEFI, (if you've disabled it). However, to allay your fears let me stress, that Installing Ubuntu with UEFI enabled is not so difficult. 
IT WILL WORK.
You can have both Windows and Ubuntu dual-booting in UEFI mode.

---

