---
title: "windows xp boot problem on ubuntu 16.04"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by iceboy64 on 2016-06-21
hi guys
I couldn't boot xp after ubuntu 16.04 installation
here is the summary:
[http://paste2.org/fn695BA4](http://paste2.org/fn695BA4)
please tell me what should I do

---

### Post by Bucky Ball on 2016-06-21
Welcome. Try booting into Ubuntu, opening a terminal, and

> sudo update-grub

Reboot and see if XP is there. After you run the command you may see it being added in the terminal.

If it is booting straight to Ubuntu and you are not getting a choice of OS at all, try hitting the shift key (from memory) just after the manufacturer splash at boot.

---

### Post by oldfred on 2016-06-21
You installed grub to the PBR- partition boot sector of the Windows NTFS partition. That cannot be done.
Windows has essential boot code in the PBR of the NTFS partition.

You may be able to use testdisk to restore the backup of the PBR that NTFS has.

       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot

---

### Post by mook765 on 2016-07-24
In your screenshot i see a logical partition ( sda5 ) starting at sector 2048. Your first partition on your drive sda1 can't be bigger than  1 MB, so your first partition can't contain your xp installation.It seems, your xp is in the logical partition sda5. Xp must be in a primary partition wich must be set to active as well, otherwise you can't boot it...
It seems that something went totally wrong with your partitionscheme before or during installtion of your linux-distribution.
if you have a backup of your xp partition, just delete the logical partition sda5 and reinstall your backup on sda1 using your rescue-disk ( or USB-stick ),hope you have one...

---

