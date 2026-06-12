---
title: "grub install fails"
date: 2019-11-26
forum: Installation &amp; Upgrades
---

### Post by davguez on 2019-11-26
Hi to all,
A few months ago I installed ubuntu 19.10 on my computer and everything used to work fine.
However, during the last apt update, an update of grub was supposed to be installed and actually failed.
When I installed my system, I did a manual partition on sda (/ and /boot/efi) with no dual boot (linux only computer) and the computer used to boot like a charm :

```

david@hpc-salon:~$ more /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=c07c2046-c498-4063-92f9-73fae5e100fe /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=AF5C-342E  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdb1 during installation
UUID=db624e1c-4dcd-4726-afa5-3b24bb9b0ddb /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c0579382-1167-49a7-8645-8af5427c96fa none            swap    sw              0       0
UUID=AF5C-342E  /boot/efi       vfat    defaults        0       1

```

however, during the grub update, I got the following message (that I can reproduce by invocing grub-install /dev/sda) :
```

david@hpc-salon:~$ sudo grub-install /dev/sda
[sudo] password for david: 
Installing for x86_64-efi platform.
grub-install: warning: efivarfs_get_variable: open(/sys/firmware/efi/efivars/blk0-47c7b225-c42a-11d2-8e57-00a0c969723b): No such file or directory.
grub-install: warning: efi_get_variable: ops->get_variable failed: No such file or directory.
grub-install: warning: get_file: could not open file "/sys/devices/pci0000:00/firmware_node/path" for reading: No such file or directory.
grub-install: warning: get_file: could not open file "/sys/devices/pci0000:00/firmware_node/hid" for reading: No such file or directory.
grub-install: warning: parse_acpi_hid_uid: could not read devices/pci0000:00/firmware_node/hid: No such file or directory.
grub-install: warning: device_get: parsing pci_root failed: No such file or directory.
grub-install: warning: efi_va_generate_file_device_path_from_esp: could not get ESP disk info: No such file or directory.
grub-install: warning: efi_generate_file_device_path_from_esp: could not generate File DP from ESP: No such file or directory.
grub-install: error: failed to register the EFI boot entry: No such file or directory.

```

I checked and there's indeed an /sys/firmware/efi/ dir :
```

david@hpc-salon:~$ ls /sys/firmware/efi/
config_table  efivars  esrt  fw_platform_size  fw_vendor  runtime  runtime-map  systab  vars
david@hpc-salon:~$ sudo efibootmgr
[sudo] password for david: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0002,0003,0001,0004,0005
Boot0000* ubuntu
Boot0001* UEFI:CD/DVD Drive
Boot0002* KINGSTON SA400S37960G
Boot0003* ST4000DM004-2CV104
Boot0004* UEFI:Removable Device
Boot0005* UEFI:Network Device

```

and I don't understand what should be the file blk0-47c7b225-c42a-11d2-8e57-00a0c969723b which is looked for and how to fix this issue.
I tried to run the boot-repair software unsuccessfully and I have posted its log to pastebin : [https://pastebin.com/dnhSw7zs](https://pastebin.com/dnhSw7zs)

I didn't rebooted my machine since as, so it stills run but I guess it won't reboot next time, and I'd like to fix grub before rebooting...
Maybe one of you can help me with this ?
Many thanks in advance...
David

---

### Post by ubfan1 on 2019-11-26
It sure looks like you have booted in legacy mode, (is the /sys/firmware/efi/efivars directory totally empty?)  I don't see how a legacy boot would have occurred, since your boot-repair report indicates no core.img piece of grub is found, and on a gpt parttiioned disk, there is no grub-bios partition anyway.  Looks like the EFI boot should work, but there are a few strange things in the EFI partition.  Those EFI/EFI/... directories seem like extras, I haven't seen that on any install before.  The other thing I'd consider is checking that EFI/BOOT/bootx64.efi matches the size of EFI/ubuntu/grubx64.efi.  Normally, bootx64.efi is a copy of shimx64.efi, but grubx64.efi must be present in the same directory, which it isn't.When shimx64.efi is bootx64.efi and grubx64.efi is present, the UEFI boot will work both with and without secure boot.

---

### Post by oldfred on 2019-11-26
Not sure what your blk0-47c... refers to?
I checked my efivars, and have nothing starting with blk, but many entries that do not match either any UUID or GUID of my system. 

But it does look like you have also installed grub in BIOS boot mode to gpt's protective MBR. And to the PBR - partition boot sector of both sda1 (FAT32 and sda3.

Linux partitions do not use PBR for anything, normally. Grub2 highly recommends not to ever install grub to PBR as it does not really fit and it uses blocklists. But you only install grub to PBR if another full install of grub is really doing booting. 

Grub in MBR, might start boot if you attempt to boot in BIOS mode, but since system really UEFI, that grub will just fail and give  a grub> entry. Just do not boot in BIOS mode as it will not work.

But the grub installed to sda1 since FAT32 may be part of issue. I know NTFS requires PBR to have Windows boot info & size of partition inside it. If grub is installed to NTFS, it corrupts Windows. 
I expect FAT32 may be the same, a with Windows that was the old DOS way of booting.
NTFS keeps a backup of the PBR, not sure if FAT32 also has that, otherwise you need to see if other Windows repair tools may fix it, or re-create it and reinstall grub from scratch.

This is what is supposed to be there, not grub.
[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)

This is for NTFS, not sure if it works for FAT32 or not.
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

I do not think this by itself can fix it, but you may also need this:
       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

---

### Post by davguez on 2019-11-29
ok, I finally found the source of the problem, it turns out that the bios was configured to boot in legacy mode, and for some reasons ubuntu didn't detected it and tried to install grub efi
so I reinstalled grub-pc with the --force option, rebooted and set the bios option to boot with efi and then purged and re-installed grub-efi which worked like a charm


thanks !

---

