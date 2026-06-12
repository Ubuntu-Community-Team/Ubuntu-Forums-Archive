---
title: "Dual-booting Ubuntu and Windows 10 with SSD + HDD"
date: 2019-09-03
forum: Installation &amp; Upgrades
---

### Post by linuxboi2 on 2019-09-03
Hello,
I bought a new Acer Aspire 7 (which came with Linpus Linux Lite) and I'd like to dual-boot Ubuntu and Windows 10 on it.
I'm not a fan of Windows - I need it for school - but still want to learn more about and use Linux as much as possible.

The laptop has a 256GB SSD and a 1TB HDD. I was thinking of installing Ubuntu and Windows on the SSD and that's also where I would install software to, and have them share the HDD for storage. The problem is I'm not sure how to do this exactly. I just never did a dual-boot before and I'm a bit confused from everything I've read so far. 

ALSO: This is what my partitions look like - [https://imgur.com/rat8M31](https://imgur.com/rat8M31)
In the manual it says not to delete the Windriver partition, as it has drivers on it, so I guess I should install them first and then reallocate that space to one of the OSs.

I would appreciate any help. Thank you,

Andreas

---

### Post by oldfred on 2019-09-03
Windows typically does not show Linux partitions.
Post this from Ubuntu live installer:
sudo parted -l

Windows will want a lot of partitions.
       [https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations) 
    
Are you booting in UEFI boot mode? 
Both Windows & Ubuntu install in the boot mode you select to boot install media, UEFI or BIOS. And then system has to be set to also boot in that mode. System boot mode does not directly control the boot mode you select to boot USB flash drive installer . But if UEFI Secure Boot is on, then you can only boot in UEFI mode. If Secure boot is off, you have both UEFI and BIOS/CSM/Legacy options.

The drivers are probably for Windows. They used to provide CD/DVD. Not required for Ubuntu.

For installing in UEFI mode see link in my signature. 

Nvidia typically needs nomodeset boot parameter, both to boot install media & first boot.

UEFI typically needs update to latest version from vendor & SSD firmware also needs update to latest version, even for new systems.You may need UEFI setting changed from RAID or Intel RST to AHCI.

Acer typically needs "trust" setting for Ubuntu UEFI boot entry.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by kurt18947 on 2019-09-04
I don't know if this is still true but in the past, the simplest was to install Windows first then install Ubuntu. GRUB should enable you to boot both. If you install Ubuntu first Windows may replace GRUB with its own boot loader which will not recognize anything except Windows. There are boot rescue disks listed in search engines, I have no recent experience with them so can't say if they work or not.

---

### Post by linuxboi2 on 2019-09-04
I'm booting in UEFI mode. Also, Secure Boot is disabled, because the bootable Windows USB wouldn't load with it enabled.
> Windows will want a lot of partitions.
       [https://docs.microsoft.com/en-us/win...Configurations]("https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations") So installing Windows is not as simple as just deleting all the partitions in the image attached (except for WINDRIVER) and giving it half of the SSD, while leaving the other half for Ubuntu?

All right, I guess first I'll have to update UEFI and SSD firmware, then I'll try to figure out "nomodest" and "trust".

Thank you very much for this.

---

### Post by linuxboi2 on 2019-09-04
I'll install windows first, then. Thank you

---

### Post by oldfred on 2019-09-04
I do not have Windows but typically give Ubuntu / about 25 to 30GB on SSD and large data partition on HDD. 

If newer user easier to put /home on HDD as that creates mount point, adds entry to fstab, and gives you ownership & permissions to use it. If you use data partition(s) you have to do all that yourself. Must be ext4 or other Linux type partition, so Windows will not be able to see that data.

Since using Windows you may also want a shared NTFS data partition on HDD. But still have to have Windows fast start up off as that sets hibernation flag on all NTFS partitions and prevents the Linux NTFS driver from writing into any NTFS partitions. Note that Windows likes to turn that setting back on with updates.

---

### Post by linuxboi2 on 2019-09-04
:o This keeps getting more complicated... Seems I'll have to take a whole day to sort it all out.

---

