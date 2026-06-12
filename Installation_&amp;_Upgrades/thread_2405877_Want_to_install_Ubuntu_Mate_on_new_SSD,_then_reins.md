---
title: "Want to install Ubuntu Mate on new SSD, then reinstall Win 10 on HDD"
date: 2018-11-12
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2018-11-12
Dell XPS i7 16GB, 1TB HDD with Win 10

I have been trying (for way too many hours now) to shrink the existing Win OS partition on the HDD to approx 100GB (more on this later) to make room for Ubuntu Mate data files and have decided to stop beating my head against a wall. No matter what options I choose, it just will not shrink to less than 600+GB.

So before installing Ubuntu Mate, I want to reinstall Win 10 on my HDD, put the OS in one partition, and use the balance for win data files and linux data files (each of these two in their own partitions). Then I will next install Ubuntu Mate on a separate SSD for dual boot. (I am assuming that this is the least problematic approach.)

When I do a clean Win 10 reinstall, will I have an option in that process to make a partition for Win 10 OS (and the two data partitions), or should I reformat the HDD and make the three partitions first and install into one of them (presumably the first?)? If the latter, what software is best for this partitioning?

I do not plan to use Win 10 much but want to keep it alive and there for when I do want it. Given that the Win OS and Win data will reside on two different partitions, how much room do I need for the OS?

Once I get the HDD sorted, will install U Mate 18.04 on a SSD and will then move into my linux questions, but need to get the HDD sorted first. I thought it good to tie the two together in case the whole picture dictates best options for any part of this

any other observations/guidance welcomed. Thanks

---

### Post by kc1di on 2018-11-12
I would partition the drive first , you can use ubuntu live usb/Dvd and use gparted to do the partitioning.  Then install windows first, Then ubuntu. Good luck.

---

### Post by Odyssey1942 on 2018-11-12
Before seeing KC1DI's post I had gone ahead with the Windows reinstall and here is what I have now

Disk O, part 1 /499MB/482/ Recovery

Disk O, part 2 / 100MB/95/ System

Disk O, part 3 /883MB/459/ MSR (Reserved)

Disk O, part 4 /58GB/58GB/ Primary

Disk O, part 5 /166GB/166GB/ Primary   (this will become the Windows data partition, I hope)

Disk 0 Unallocated / 706.9GB/706.9GB   (this will become the linux data partition, I hope)

If memory serves, only 3 primary partitions are allowed. If correct, do I need to change anything so that I can use the unallocated later for another partition (for linux data)? And if so, what please?

---

### Post by Mark Phelps on 2018-11-12
When you go to reinstall Win10, since you already have an NTFS-formatted partition, it will give you the option to install to that partition.

It should also give you the option to reformat that partition -- and option you should accept.

Also, if you're not going to install much in Win10, you can use a 40GB partition and that will provide plenty of room for growth.

---

### Post by Odyssey1942 on 2018-11-12
I am planning to install Windows in Partition 4. 

Any thoughts on the Primary partition question?

---

### Post by Odyssey1942 on 2018-11-12
Mark, I must have missed line 2 of yours, and I seek clarification. Please help me understand the purpose of the reformatting at that point. (unfortunately I am well past that now as I have already installed, but want to learn [and can do over if important]). Thanks.

---

### Post by oldfred on 2018-11-12
With UEFI and gpt there is no primary partitions, in effect all partitions are primary and the new limit is 128 partitions with default gpt partition table.
Windows requires gpt for UEFI installs.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by Odyssey1942 on 2018-11-14
oldfred, if I understand your link to "UEFI/GPT-based hard drive partitions", the second (new 120GB SATA SSD) drive for Ubuntu Mate can be either BIOS or UEFI. The HDD (with Win10) in this computer is UEFI. Do you recommend going with UEFI or BIOS for UM (or must it be one or the other) for the SSD? Thanks.

---

### Post by oldfred on 2018-11-14
I changed to use gpt with my BIOS only system back in 2010. My XP was on a separate MBR drive.
I wanted a new UEFI system, but in 2011 added a small SSD for / and it improved my old system so much, I did not build a new UEFI system until 2014.
But as soon as Microsoft required all new installs to be UEFI on gpt drives in 2012 with Windows 8, I started adding both the bios_grub partition for my BIOS system, but also added the ESP - efi system partition so I could move drive to new UEFI system without totally erasing & starting over.

I highly recommend gpt.

And if Windows is UEFI, best to have Ubuntu in UEFI boot mode on gpt drive.

If you use gpt and have both the bios_grub & ESP, you just have to reinstall correct version of grub to convert from UEFI to BIOS or vice-versa. 
BIOS on gpt requires a 1 or 2MB unformatted partition with bios_grub flag. UEFI requires an ESP, FAT32 with boot flag. Windows default is 100MB, if large drive I suggest 300 to 500MB if planning any thing other than total standard single system boot. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Odyssey1942 on 2018-11-14
Fred, I had only just begun to understand how to move around the BIOS interface semi-comfortably when UEFI was introduced and I am still wondering what UEFI is. Unfortunately GPT and EFI are totally meaningless to me. I read the links, but my meager experience doesn't afford me much benefit from the reading.

I cannot be sure from the 16.04 install 30 or so months ago, but don't remember having a choice between BIOS and UEFI during the install. Is that a selection I need to make in BIOS before starting the install?

I am pretty sure that EXT4 was the best formatting option for 16.04, and without guidance to the contrary. will choose EXT4 again. (I know format is a different subject, but do remember that I will need to make that choice during the install)

My questions, at this early stage, are how/where do I choose UEFI over BIOS (or will my computer default to UEFI) in (or before) the install; and will I face a choice between GPT and EFI in (or before) the install? Thanks.

---

### Post by oldfred on 2018-11-14
Only if you partition in advance can you select gpt with BIOS installs.
Normal install in BIOS mode will use MBR and UEFI will use gpt partitioning. But drives over 2TB will have to be gpt.

gpt is the new replacement for MBR partitioning which has been the standard since the IBM PC came out in the early 1980's.
       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

Link in my signature has lots more info & further links, see last section on Acronyms. 

The Ubuntu live installer is configured for both UEFI boot and BIOS boot on DVD or flash drive.
It uses grub for UEFI boot and syslinux for BIOS boot.
UEFI will see a boot loader in MBR and /EFI/Boot/bootx64.efi in ESP, so will show two boot options for flash drive or DVD. One normally is clearly UEFI:flash and other may be just flash where flash is name or label of flash drive or DVD drive. 



Basically UEFI is the new replacement for BIOS. But it has backward compatiblity, so you can use an old install. 
Generally if you have newer UEFI hardware, you should install in UEFI mode. But a few dislike change  and know BIOS/MBR so stay with it.
Intel has suggested that new systems in 2020 become Class 3 or no BIOS option. 

Arch often has good explanations:
       [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

Attached screen shot shows a user with a Toshiba flash drive and the two boot options.

---

### Post by Odyssey1942 on 2018-11-15
As I explore how to find fast boot, I see that:

> fast boot in bios means PC ignores USB devices except for mouse/kb at startup

so if the computer will boot from a USB, nothing further needed?

---

### Post by oldfred on 2018-11-15
Fast boot assumes that there is no hardware or other configuration change. 
Normally BIOS or UEFI scan system for all hardware and write that info onto drive for operating system. But with UEFI fast boot it just jumps to booting system without new scan. That also then is so quick that you do not have time to press a key to get into UEFI or UEFI boot key.
My system allows different settings for cold (full power on) and warm reboot and time delay if fast boot on, so I can still press a key.

You at least want normal boot after full power down, just so you can get back into UEFI or UEFI boot menu.

Normally with UEFI, a separate setting is required to turn on allow USB boot, particularly if UEFI Secure Boot is on.

---

### Post by Odyssey1942 on 2018-11-15
Oldfred, interesting as always. 

Turning back to the HOW of installing the SSD, may I assume that, if the computer will boot into the USB stick, then I do not need to do anything about fast boot?

---

### Post by oldfred on 2018-11-15
If you have the choice to boot, I would go ahead.

But if UEFI Fast Boot is on, and you have issues getting into UEFI or UEFI boot menu, often a full cold boot, if laptop remove battery, and hold power switch to drain power works. Microsoft requires Fast Boot, so you must have it somewhere.

A few cases users had to jumper pins on motherboard or remove motherboard coin battery to totally reset UEFI/BIOS.

---

### Post by Odyssey1942 on 2018-11-15
Thanks, I did go ahead and it booted from the USB drive, and it seems to be installed OK.

---

