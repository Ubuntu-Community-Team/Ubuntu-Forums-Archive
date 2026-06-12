---
title: "if you dont want to dual boot windows"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by boregard on 2012-07-23
hello, if i just want to have Ubuntu  on my computer do i need a fat32 partition? what partitions do i need for a uefi/gpt hd? any advice will be greatly appreciated. best regards

---

### Post by lukeiamyourfather on 2012-07-23
No, you don't need FAT. The recommended file system right now is ext4.

---

### Post by oldfred on 2012-07-23
If your system is UEFI, then the first efi partition is FAT32. Most UEFI systems also boot in BIOS/MBR mode or if only Ubuntu you can use BIOS/gpt to boot. Windows only boots from gpt partitioned drives with UEFI. If system is UEFI capable then I would create both efi & bios_grub, but only once will be used depending on which way you boot. 

Otherwise you only want Linux formated partitions as you would need a copy of Windows or Windows repairCD to run chkdsk or make other repairs to Windows formated partitions.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)
AsRock calls BIOS mode AHCI.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
(Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

---

### Post by boregard on 2012-07-23
okay, i reinstalled ubuntu once before and had trouble getting it to boot so i used gparted and created a1 MB bios_grub  no format & that solved boot problem. but my problem of misaligned partitions still exist. so if i partition hd in advance wont reinstalling ubuntu with live cd delete the partitions i created. so i guess my question now is do i have to choose advanced partitioning during installation? if so could someone suggest a tutorial that  would be good for someone that has never used this option before? sorry , i hope my question is making sense.

---

### Post by lukeiamyourfather on 2012-07-23
> **lukeiamyourfather said:**
> No, you don't need FAT. The recommended file system right now is ext4.

I read the original post as if the FAT partition was for Windows (not UEFI booting). My bad.

---

### Post by simonmoon42 on 2012-07-23
> **boregard said:**
> okay, i reinstalled ubuntu once before and had trouble getting it to boot so i used gparted and created a1 MB bios_grub  no format & that solved boot problem. but my problem of misaligned partitions still exist. so if i partition hd in advance wont reinstalling ubuntu with live cd delete the partitions i created. so i guess my question now is do i have to choose advanced partitioning during installation? if so could someone suggest a tutorial that  would be good for someone that has never used this option before? sorry , i hope my question is making sense.

It will only delete the partitions if you tell it to. If you tell it to install to an existing partion, it will.

[This is a short explanation of partitioning. Hopefully it will help.]("https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning") I know your situation is a little different. But for the most part, once you get the GRUB/UEFI/BIOS situation sorted, it should be a standard install from there.

---

### Post by oldfred on 2012-07-23
What partition is mis- aligned? If the extended it does not matter as you actually write into all the logicals in the extended. The current versions of gparted & gdisk all use correct alignment.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by boregard on 2012-07-23
> **oldfred said:**
> What partition is mis- aligned? If the extended it does not matter as you actually write into all the logicals in the extended. The current versions of gparted & gdisk all use correct alignment.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print here is mere info on which partitions are misaligned that may help,   BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): v

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 2 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Caution: Partition 3 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.

Consult [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
for information on disk alignment.

No problems found. 1 free sectors (512 bytes) available in 1
segments, the largest of which is 1 (512 bytes) in size.

---

### Post by oldfred on 2012-07-23
Is this drive a newer 4K or a SSD drive? Then you may need to adjust.

If an older drive it will not really matter. Partitions must be from over 2 years ago as all the newer versions of gdisk & gparted align correctly by default.

---

### Post by boregard on 2012-07-24
> **oldfred said:**
> Is this drive a newer 4K or a SSD drive? Then you may need to adjust.

If an older drive it will not really matter. Partitions must be from over 2 years ago as all the newer versions of gdisk & gparted align correctly by default. sorry for taking so long to get back, it's a newer one. i have managed to create partitions with gdisk and used the v option to verify that they are aligned correctly. now if i can write them to disk without reinstalling i may be ok.

---

### Post by boregard on 2012-07-27
I have one more question i cant find answer to through the links suggested. if i partition in advance and choose erase and install ubuntu when using live cd/dvd, does that mean it will not recognize the partitions i created in advance? sorry for all the noob questions.

---

### Post by oldfred on 2012-07-27
I always partition in advance. You really do not have to format at that point if you are using partition for the Linux install, but I usually do.

But you then have to use Something Else or manual install. All the autoinstalls just do their own thing, either erase entire drive, or try to repartition to share drive, or use unallocated space. I never trust the auto install and know what I want so I partition in advance. 

Manual install also lets you create partitions, so you do not have to do it in advance. But it only has the LInux driver as part of the installer. So if creating a NTFS partition for Windows or a shared NTFS for shared data, you either do that in advance or leave unallocated when using the installers partition tool.

---

### Post by boregard on 2012-07-27
> **oldfred said:**
> I always partition in advance. You really do not have to format at that point if you are using partition for the Linux install, but I usually do.

But you then have to use Something Else or manual install. All the autoinstalls just do their own thing, either erase entire drive, or try to repartition to share drive, or use unallocated space. I never trust the auto install and know what I want so I partition in advance. 

Manual install also lets you create partitions, so you do not have to do it in advance. But it only has the LInux driver as part of the installer. So if creating a NTFS partition for Windows or a shared NTFS for shared data, you either do that in advance or leave unallocated when using the installers partition tool. i tried the something else option when installing with live cd/dvd and could not find a way to make to make the starting sector 1mb or 2040. my problem is that i always wind up with a start sector of 34 and that makes all the following sectors misaligned.

---

### Post by boregard on 2012-07-28
okay,sorry for taking so long to get back but i have been busy. well i partitioned the hd in advance like suggested but this time during installation i chose advanced option. i didn't touch anything but clicked on install now, then it requested me to pick a partition for root and i made my choice & checked the box to format. i double checked start sector to make sure it was 1mb. when it finished installing i checked in disk utility and everything was aligned. so thanks oldfred & everyone else for your patience and help. best regards

---

### Post by oldfred on 2012-07-28
Glad that worked. :)

---

