---
title: "cannot boot on windows after installing ubuntu 16.04"
date: 2016-08-23
forum: Installation &amp; Upgrades
---

### Post by es22 on 2016-08-23
hello,

I just installed ubuntu 16.04 over an old version of fedora, my sony vaio has also a windows 7 version.
 unfortunately, now i cannot boot on windows. i'd tried to run boot-repair but still does not work. the only operating system that works is ubuntu. 
i'd run boot-info and posted the results here:

[http://paste2.org/IGI7G3Dj](http://paste2.org/IGI7G3Dj)

i'll appreciate any help.

regards,

ernesto

---

### Post by speed... on 2016-08-23
Hi,

when the machine boots up do you see the boot menu (can you choose Windows or the Ubuntu recovery mode)?

/Edit: You can also try the steps mentioned here -> [https://ubuntuforums.org/showthread.php?t=2215230](https://ubuntuforums.org/showthread.php?t=2215230)

---

### Post by grahammechanical on 2016-08-23
The Grub configuration file that is used to create the Linux boot menu does have an entry for Windows. Grub is set to look for Windows boot files in sda1. And the Windows boot files are there.

The problem could be caused by Grub being installed in 2 places. The MBR of sda and the partition sda1. I do not think that Grub likes working from a partition. I may be wrong. Try loading Ubuntu and running these two commands

```
sudo update-grub
sudo grub-install /dev/sda
```

Watch the printout. It should list Windows as a detected OS.

Regards

---

### Post by mook765 on 2016-08-23
You installed Grub-boot-loader to sda1.
The Grub-boot-loader which appears on sda is a left-over from your fedora-installation.
Use the commands suggested by grahammechanical, but in different order:
```
sudo grub-install /dev/sda
sudo update-grub
```
If you run 'sudo update-grub' first, this will update the Grub-boot-loader which is installed on sda1, this is not useful.
Installing Grub to sda1 overwrote essential code off your Windows. You may need a Windows-recovery-CD to repair that.
Kind regards...

---

### Post by oldfred on 2016-08-23
You cannot have grub in a NTFS PBR - partition boot sector. 
Windows has essential Windows boot info in the PBR or your sda1.
NTFS partitions do have a backup of the PBR, so you can usually use testdisk to restore the backup PBR.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Note: It may say grub in partition is valid, as grub can be installed to PBR, but is not recommended. It just is that in a NTFS partition, it will not be valid to boot Windows.

---

