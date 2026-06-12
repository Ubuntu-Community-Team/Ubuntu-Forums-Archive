---
title: "GRUB on EFI SSD can't boot Windows on msdos HDD"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by cyrnihao on 2013-08-30
Hi,
I have an IdeaPad U310 with Intel Rapid Boost stuff installed. The hardware includes both a solid state (SSD, 30GB) and normal HDD (500GB), but it seems that Windows only used the SSD for caching or something like that (an 8GB partition NTFS plus 21GB unallocated). Originally I wanted to install Ubuntu on the HDD alongside Windows, but that required deleting the Lenovo recovery partitions and utitiles to create an extended partition, which did not seem like a good thing to do. So I decided to use the SSD for Ubuntu only and chainload Windows on /dev/sdb, the HDD. 

Unfortunately Ubiquity did not detect a partition table on /dev/sdb (table blank, buttons greyed out), and did not show /dev/sda as an installation target at all in the dropdown. Fdisk -l and Gparted both showed the systems, though. Deleting everything from the SSD in Gparted and creating an ext4 partition for Ubuntu also did not work for Ubiquity, which did the same thing again. The only thing that worked was to delete the partition table (formerly msdos) on the SSD and create a new GPT table with an EFI boot sector, ext4 partition, and some swap. Ubiquity then detected sda and allowed Ubuntu to be installed there, on the SSD. GRUB detects WIndows but when I try to boot it, I get the error "Invalid EFI path." It also used to show an error, "Partition not found," but that was fixed by disabling RAID/RapidBoost in the BIOS.

Any suggestions on how to get Windows booting? I thought chainloading the Windows bootloader on the msdos HDD from the EFI GRUB on the SSD would work, but it doesn't.

Thanks!

---

### Post by oldfred on 2013-08-30
If it is Windows 8, the hard drive should be gpt partitioned not MBR. And with gpt you do not have extended partition and logical partitions.

You do have to remove the RAID meta-data from both drives that Intel SRT has added.

This user posted this:
 [http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

See also my signature for more details.

Some other lenovo threads.

  lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)

May be best to post link to BootInfo report.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by cyrnihao on 2013-08-30
Thanks, reading through this info. FYI it is not WIndows 8, it is Windows 7.

EDIT: Ok, this is doable. May have to redo the Ubuntu install but that's ok.

---

### Post by oldfred on 2013-08-30
Only a few Windows 7 systems were UEFI, so then you need to use Boot-Repair to convert your Ubuntu install from UEFI to BIOS.
Windows only boots from gpt with UEFI.
Ubuntu can boot from gpt with UEFI or BIOS.
Both systems boot from MBR only with BIOS.

To fix Ubuntu to boot in BIOS mode you will need a tiny 1MB unformatted partition on the gpt drive with the bios_grub flag. Do that first, then you can run Boot-Repair and it can uninstall grub-efi and install grub-pc for BIOS. Or you can reinstall in BIOS mode.

---

