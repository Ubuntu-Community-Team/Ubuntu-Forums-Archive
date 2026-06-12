---
title: "Trouble Booting 16.04.1"
date: 2017-02-11
forum: Installation &amp; Upgrades
---

### Post by ImTroyMiller on 2017-02-11
I've been using Ubuntu since 12.04 and have noticed that on each install(I update on LTS releases) that I've always had an issue with Grub. After I boot my PC, I always get an error and the "grub rescue>" prompt. Usually I just pop in my Boot-Repair-Disk, click the repair button and everything is good to go, but on 16.04.1 it isn't working. It seems to be some type of UEFI issue and I'm still a bit confused about it.

My motherboard is a Gigabyte 970A-D3 and it is labeled "Dual UEFI Bios". In the past, I believe I've been using legacy. The exact error I'm getting after I install 16.04.1LTS and try to boot is...

> error: file '/boot/grub/i386-pc/normal.mod' not found.
Entering rescue mod...
grub rescue>

This seems strange because I have an AMD processor and I used this same disk to install Ubuntu on another machine that also has an AMD processor.

I have three hard drives in my PC and I'm installing Ubuntu onto one of those(sdb1, with sdb5 being /boot), one of the other hard drives is just for backing up data(75GB), and the other hard drive has Ubuntu 14.04(my soon to be previous OS). The previous boot partition was on sdb but I purposely wiped it for this installation.

So when I boot up my Boot-Repair-Disk and click on the recommended repair button, I get an error message that says...

> The boot of your PC is in Legacy mode. Please change it to EFI mode. Please use Boot-Repair-Disk64bit([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")) which contains as EFI-compatible version of this software.((use it from live-USB, not from DVD))

When I change the 'Boot Mode Selection' in bios from 'UEFI and Legacy' to 'UEFI Only', save and reboot back into bios, I can no longer see either of my two CD-ROM Drives and I can only see one of my three hard drives(the 75GB one), and when I change the 'Boot Mode Selection' in bios to 'Legacy Only' I can't see this 75GB hard drive but I can see all of my drives and my CD-ROM drives. On previous installations it has been in 'UEFI and Legacy' mode, so I was able to see all of my hard drives and CD-ROM drives.

I have not downloaded the new Boot-Repair-Disk yet because I had thought that I was already using it. It appears to have last been updated back in 2014. After posting this I'm going to give it a try, but I'm confused if I should change my bios to 'UEFI-only' mode, run the Boot-Repair-Disk disk from USB, and then afterward change it back, or do something else.

Also in my bios, I have different options that have choices to change UEFI/Legacy settings. They are 'Boot Mood Selection', 'Storage Boot Option Control'(which contains these options > Diasabled, UEFI Only, Legacy Only, Legacy First, UEFI First), and 'Other PCI Device ROM Priority'(which has two options > UEFI OpROM and Legacy OpROM). What should these be set to?

Also, am I correct when I refer to my motherboards firmware as 'bios'?

---

### Post by oldfred on 2017-02-11
UEFI has replaced BIOS, so if UEFI then it is UEFI. But some vendors still call it BIOS as that is the term still used. And so far UEFI has CSM, so older BIOS boot can still be used for now.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  


Your motherboard seems to need IOMMU setting changed in UEFI and a boot parameter to work correctly. Not sure if related to your boot issues or not.

But with UEFI you must have the ESP - efi system partition which is a FAT32 formatted partition with boot flag if using gparted. Boot flag is really just assigned some very long GUID, so UEFI knows which partition is the ESP and where to look for boot files.
But Ubuntu's grub only installs its .efi boot files to the ESP on drive seen as sda. I have installed multiple times to sdb, and flash drives as sdc thru sde and invariably it overwrites my main Ubuntu's /EFI/ubuntu folder. I quickly learned to backup. 
But if dual booting with Windows they are in separate folders so no issue of sharing the ESP on sda.

But if installing to a drive seen as sdb, but sda does not have an ESP, you will not be able to get grub installed. There may be some major work around, but easier just to add an ESP/FAT32 partition to sda. But better if sda is gpt partitioned as that is the standard for UEFI.
I converted to only using gpt on new & reformatted drives and larger flash drives back with my BIOS system in 2011. But did not get my first UEFI system until about 2014.

Normal not found it typically an old install of grub in the other boot mode UEFI or BIOS, and new install in other mode. So then old grub does not work with new files, or UEFI and BIOS are not compatible.

Best to just add Boot-Repair to your current live installer, so running same version of Ubuntu. And be sure to boot in same mode as you installed, either UEFI or BIOS. And then always boot flash drives & hard drives in that mode.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ImTroyMiller on 2017-02-12
I got it working by following the instructions that the error gave me.  I downloaded the newest version of Boot-Repair-Disk, put it on a flash drive, and then booted to the flash drive.  It repaired without problems but it did place the boot partition on sdc(must be because that happened to be of FAT32 format and the rest are EXT4).

SO UEFI only recognizes FAT32 partitions?

---

### Post by oldfred on 2017-02-12
UEFI only boots from a FAT32 formatted partition with the correct very long GUID for the ESP - efi system partition.
Parted/gparted use boot flag to assign GUID.
Gdisk uses code ef00 to assign GUID.

At bottom of link in my signature are links to various Acronyms and definitions.        ESP/efi -  Efi System Partition [https://en.wikipedia.org/wiki/EFI_system_partition](https://en.wikipedia.org/wiki/EFI_system_partition)

---

