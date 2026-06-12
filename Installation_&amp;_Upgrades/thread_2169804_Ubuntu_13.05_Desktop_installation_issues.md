---
title: "Ubuntu 13.05 Desktop installation issues"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by geohei on 2013-08-23
Hi.

I test installed Ubuntu 13.04 Desktop on an UEFI system.

```
...
Command (? for help): p
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7B0E6510-D248-42E6-BB41-8F1545A740AA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 38072941 sectors (18.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI System - Windows
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       210184191   100.0 GiB   0700  Basic data partition
   4       210184192       315041791   50.0 GiB    0700  Basic data partition
   5       315041792       315246591   100.0 MiB   EF00  EFI System - Ubuntu
   6       315246592       420104191   50.0 GiB    0700  Ubuntu
   7       420104192       462047231   20.0 GiB    8200  Linux swap
```

Some issues/questions raised.

1. I selected sda6 to install / and format the partition. However the following message showed up: "Write previous changes to disk and continue? Before you can select a new partition size, any previous changes have to be written to disk. You cannot undo this operation. Please note that the resize operation may take a long time. <Go Back> <Continue>". Actually, I didn't touch any of the partitions to resize! Why this message. I go back and do the same thing again, but then the message doesn't appear. What's wrong here?

2. I choose /dev/sda6 as "Device for boot loader installation:". However the bootloader (grubx64.efi) is not saved to that partition! It's saved in /dev/sda1 (121856 bytes).

3. Worse ... The Ubuntu installation doesn't put an entry into UEFI BBS, hence, I cannot start the installation after reboot!

In 12.04, only point 2. was a problem. 1. and 3. were properly handled!

Any ideas?

Thanks,

---

### Post by oldfred on 2013-08-23
You refer to srs5694's comment that two efi partitions are allowed but not recommended. I have not seen a working system with two and the few that tried creating two all have had issues. So even if allowed, it does not seem any of the installers or UEFI boot loaders work with two currently.
Previously srs5694 in this forum said only one efi partition per drive, but that was older info, so standard may have also changed, but software has not.

I am not sure why you would even want multiple ESPs. You can add multiple boot loaders into the one esp. I think you could just create ubuntu1, ubuntu2 etc if you wanted to boot different systems from UEFI menu, but you do not need to as grub menu handles all the different installs you may have.

---

### Post by geohei on 2013-08-23
You closed my other thread ([http://ubuntuforums.org/showthread.php?t=2169419):](http://ubuntuforums.org/showthread.php?t=2169419):)
> thread closed. You started a new thread on similar related issues.
The key question there was how the bootloader finds the partition it's supposed to boot.

This thread however deals with 13.04 installation issues regarding UEFI implementation.
This is definitely a different subject and subsequently set of questions!
It would be OT to answer those questions here and/or vice versa.
I tried to keep separate what doesn't belong together. The only common point is that it's about the same system (UEFI, GPT, multiboot, 2 ESPs).

But as you wish ... :)

Ok, back to this subject.

I'll try tomorrow to install 13.04 on UEFI system with only one ESP. Then we can continue ...

---

### Post by oldfred on 2013-08-23
The boot loader finds the ESP which is the efi partition. I have yet to see any system that can tell apart two efi partitions even it that is the standard. There are a lot of UEFI specifications that are not being followed. Just remove the boot flag from your second efi partition and run Boot-Repair when booted in UEFI mode.

---

### Post by geohei on 2013-08-24
> **oldfred said:**
> The boot loader finds the ESP which is the efi partition. I have yet to see any system that can tell apart two efi partitions even it that is the standard. There are a lot of UEFI specifications that are not being followed. Just remove the boot flag from your second efi partition and run Boot-Repair when booted in UEFI mode.
You are right that many systems don't cope with 2 ESPs. Also Windows 7 has its problems.

I did some more testing. 

I followed your advise to get rid of the boot flag of the second ESP (using gdisk. Code set from ef00 to 0700 - boot flag gone confirmed by gparted). However all this didn't change anything.

```
...
Command (? for help): p
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7B0E6510-D248-42E6-BB41-8F1545A740AA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 38072941 sectors (18.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI System - Windows
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       210184191   100.0 GiB   0700  Basic data partition
   4       210184192       315041791   50.0 GiB    0700  Basic data partition
   5       315041792       315246591   100.0 MiB   0700  
   6       315246592       420104191   50.0 GiB    0700  Ubuntu
   7       420104192       462047231   20.0 GiB    8200  Linux swap
```

_1. of initial article_ - I found out that this message always shows up as soon as I select a partition as root (selecting format or not - doesn't change). The message talks about "resize". No resize attempt ever occurred in my case. I never resized during installation process or tried to do so. This message is highly misleading especially since it talks about actions (resize, format, install) which cannot be undone in relation to partitions/devices. BTW ... it's also no alignment issue.

Is it possible that this message doesn't show up during Ubuntu 13.04?

If yes, I did something wrong and would like to know what this could be.

_2. of initial article_ - The bootloader is always saved to sdb1, also if I select sdb (the device) or sdb5 (before it was flagged 0700 = !boot). So ... why does the Ubuntu installer offer the user the misleading possibility to select a partition for the bootloader when it always takes sbd2 (in my case) whatever the user elects?

_3. of initial article_ - Whatever I did, the UEFI entry never made it to the NVRAM.

BTW ... Boot-Repair might do a good job, but it doesn't always help. Also (and this excludes it from my preferred tools), I don't exactly know what it does (black box principle). I'd rather modify the relevant configurations manually myself after having understood how it works.

---

### Post by oldfred on 2013-08-24
I think it just is a standard partitioning comment. It does not know if you are resizing, or just formatting as you have not processed anything until you proceed. I partition in advance and have not notice messages when formatting and selecting /, but I know that is all I am doing.
Tools post two alignment comments. One very old from fdisk on cylinders. That comment goes back to before drives changed to LBA - large block allocation with happened when drives went over 8GB. The newer sector alignment issue is related to the new 4K drives and SSD. Partitions should be on 8 sector blocks and all the new partition tools do that. Some with MBR may show extended partition mis-aligned but you do not write to extended partition and as long as all the logicals are aligned it is fine.

If you have secure boot on, it only shows systems that are secure boot. If Ubuntu is not secure boot version it will not show. But if secure boot is off it should show. Some examples others have posted.

---

