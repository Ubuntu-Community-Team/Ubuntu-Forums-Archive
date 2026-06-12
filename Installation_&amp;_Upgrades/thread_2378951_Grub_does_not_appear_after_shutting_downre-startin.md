---
title: "Grub does not appear after shutting down/re-starting Ubuntu, always boots to Windows"
date: 2017-11-29
forum: Installation &amp; Upgrades
---

### Post by davidromerot on 2017-11-29
Hello there,

I have a problem when my new dual-boot installation. I have a Sony VAIO SVF-14N. I wiped out the hard drive, and did a fresh install of Windows 10 and Ubuntu 167.04 LTS. Everything went well, except for a booting problem, which is unlike any other booting issue I found in the forums.

Whenever I am in Ubuntu and I re-start or shut-down the machine, the next boot goes directly to Windows 10, without the Grub menu ever showing up.
Whenever I re-start or shut down my machine from Windows, the Grub menu does appear in the next boot and I can choose to go to Ubuntu or Windows 10.

So, in short, for some reason Windows 10 is playing nicely with Grub and Ubuntu isn't.

Can anybody guess what the problem might be?

Thanks in advance.

---

### Post by irv on 2017-11-29
Have you checked your BIOS? The boot order should be set to Ubuntu first and then Windows.

---

### Post by oldfred on 2017-11-29
Are both systems BIOS or both UEFI?

Sony is one that violates UEFI standard that says NOT to use Description as part of boot. And only valid description is "Windows Boot Manager".
But your issues seems more like systems are not both UEFI?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by davidromerot on 2017-11-29
Thanks oldfred and irv for your replies.

Here is the result of boot-info:

[http://paste.ubuntu.com/26075409/](http://paste.ubuntu.com/26075409/)

Should I apply the suggested repairs? Would they fix the specific problem I have, or are there just generic repairs to optimize the boot?
Is boot-repair safe? I wouldn't want to risk applying these repairs if there is a good chance it could damage my current boot (which is sort of usable)...

Thanks!

---

### Post by yancek on 2017-11-29
Part of the problem is the fact that you have two EFI partitions on the same drive which is a bad thing.  I don't know why the Ubuntu efi files were not installed to the original EFI partition (sda1)  You also have Grub installed on the second EFI partition (sda2) which is something I've never seen before and isn't correct.  There are several possibilities but I'm not versed enough in UEFI to feel confident about suggesting any so wait for some like oldfred to replay back.

---

### Post by oldfred on 2017-11-29
Some vendors have a second FAT32 partition with vendor utilities and .efi files. But it is not flagged as the ESP - efi system partition. Not sure how vendor does it, it may just move boot flag to vendor partition to make it ESP when booting vendor utilities, or just have UEFI use vendor partition even if not UEFI ESP.

But you install grub-pc for BIOS boot into the partition boot sector (PBR) for the ESP. That probably corrupted the FAT32 partition as Windows types of partitions must have Windows boot info in PBR.
[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)

I know this works for NTFS, but not sure if FAT32 also has backup PBR. I found that FAT32 may have backup.

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


The other alternative is to fully backup the ESP, delete the ESP, recreate FAT32 partition and assign boot flag to make it ESP, and restore all files/folders. But UEFI uses gpt's GUID which is unique, so you may have to delete old entries in UEFI and create new ones with efibootmgr or possibly from inside UEFI.

---

