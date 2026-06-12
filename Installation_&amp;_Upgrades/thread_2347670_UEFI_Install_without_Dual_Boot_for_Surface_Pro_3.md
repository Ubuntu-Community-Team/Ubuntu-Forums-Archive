---
title: "UEFI Install without Dual Boot for Surface Pro 3"
date: 2016-12-27
forum: Installation &amp; Upgrades
---

### Post by kutos85 on 2016-12-27
Hi All,

I've been trying to figure out how to install Ubuntu 16.04 64-bit directly onto the SSD of my Surface Pro 3. Unfortunately all the guides I've found are for dual boot setups. So far I've disabled "Secure Boot Control" in the EFI boot menu and have done the following.

1) Got to the partition section I selected "Erase disk and install Ubuntu" and continued with the installation. After it finished installing, I rebooted and it started directly in the EFI boot menu.

2) Tried selecting "Something else" in the partition section of the installer and manually setup the partitions to 

/dev/sda
 free space                     1MB
 /dev/sda1  efi                510MB
 /dev/sda2  swap             8192MB
 /dev/sda3     /     ext4     247355MB

Device for boot loader installation: /dev/sda1

3) Same steps as 2 except I did the efi partition as fat32 with /boot/efi as the mount point.

Each time after the installation is complete it boots straight into the EFI boot menu. Any help would be greatly appreciated.

---

### Post by oldfred on 2016-12-27
You realize that is a Microsoft system.
Back in DOS days it would not release a new version of DOS until competing software would not work in its version. (Documented in court case.)
And it has somewhat improved in recent years, but not totally easy to work with.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[URL="https://help.ubuntu.com/community/Boot-Info"]https://help.ubuntu.com/community/Boot-Info

      [/URL]
 Surface Pro Ubuntu install:
Surface Pro 3 - USB/MicroSD Only Install 
[http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
Surface Pro2 mega thread:
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247) 
    [URL="https://help.ubuntu.com/community/Boot-Info"]
[/URL]

---

### Post by kutos85 on 2016-12-27
Here is the BootInfo summary report [http://paste2.org/vaUxVMbW](http://paste2.org/vaUxVMbW)

---

### Post by oldfred on 2016-12-27
You have mixed UEFI and BIOS.

Your fstab shows the mounting of the ESP - efi system partition which is FAT32 formatted as sda1.
But you have installed grub for BIOS (incorrectly) into the FAT32 partition's boot sector. 
And then you have installed grub to the protective MBR of the gpt partitioned drive, which is only correct if you also have a 1 or 2MB unformulated partition with the bios_grub flag.

Almost all my installs (only desktops) have both the ESP & bios_grub as first two partitions. I started that when I still booted in BIOS mode but thought I might move drive to newer UEFI system. And still do that to newer UEFI system, but more just in case later I want to experiment with BIOS.

You probably want UEFI boot. But I do not know if FAT32 has backup of partition boot sector PBR or BS. If it does then use testdisk to restore like instructions for NTFS.

If not backup sda1's files. Delete sda1, create new sda1 as FAT32 with boot flag to make it a new ESP. Not sure if restoring files will work. But best to use Boot-Repair to uninstall/reinstall all of grub using advanced options. Internet must be working as it downloads a new copy of grub. And be sure to boot installer/Boot-Repair in UEFI boot mode.

Be sure to always boot in UEFI mode, not legacy mode. UEFI with Secure Boot off, should offer two boot modes BIOS and UEFI for installer flash drive.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

And once fixed, be sure to have system booting in UEFI mode, usually with Secure Boot off works better.

Testdisk for NTFS, not sure if works for FAT32.
 PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by kutos85 on 2016-12-27
Your solution is a little advanced for me and is going over my head. Is there a way I can manually setup the partitions using the Ubuntu installer to boot into UEFI without a NTFS partition or Windows installation?

---

### Post by oldfred on 2016-12-27
Your 1) or 2) installs both look correct.
But you have to boot in UEFI mode to install in UEFI mode.
And specify grub to install to drive like sda not to a partition. With Something Else that should also be the default setting.

But your system may not want to directly boot ubuntu entry in UEFI.
If you want to reinstall/repartition that will clean up the issues. The rerun Boot-Repair and in advance mode click on the "use standard efi file". If you have a boot entry to boot hard drive or fallback try that not the ubuntu entry in UEFI menu.

Then post new copy of Summary report from Boot-Repair.

---

### Post by kutos85 on 2016-12-28
[http://paste2.org/kUx04wUX](http://paste2.org/kUx04wUX)

The Boot Repair popped up with an error
Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB-250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].

---

### Post by oldfred on 2016-12-28
You may be able to run chkdsk from a Windows repair disk or dosfsck from Ubuntu:
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

If that does not unlock it, then we have to delete sda1 & recreate it.

You also do not have an Ubuntu boot entry nor the fallback/hard drive UEFI entries, to see your entrie without running full report:

 sudo efibootmgr -v  

Total reinstall of grub should create the Ubuntu entry, but Microsoft may not let you use it. So only fallback will work which Boot-Repair should copy files, but will not add UEFI boot menu entry.

 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
     'Use the standard EFI file' in advanced options. 

 You can add your hard drive UEFI boot entry to boot fallback file:
sudo efibootmgr -c -g -d /dev/sda -p 1 -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'

    see also 
man efibootmgr

---

### Post by kutos85 on 2016-12-28
Thank you for all your help. I think I might be better reinstalling windows and doing a dual boot. All this information you are providing me is a little too advanced for me. I'm trying to get Ubuntu installed to get familiar with Linux.

---

### Post by oldfred on 2016-12-28
This is then a crash course. :)

You will have some of the same issues dual booting. But if just starting out better to dual boot.

---

