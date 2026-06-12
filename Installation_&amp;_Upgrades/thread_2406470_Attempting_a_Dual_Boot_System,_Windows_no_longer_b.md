---
title: "Attempting a Dual Boot System, Windows no longer boots...http://paste.ubuntu.com/p/bJ"
date: 2018-11-21
forum: Installation &amp; Upgrades
---

### Post by merrem2 on 2018-11-21
[http://paste.ubuntu.com/p/bJZqGhg3Tn/](http://paste.ubuntu.com/p/bJZqGhg3Tn/)

Following the advice in boot repair, I've got two OS's at the moment,

Windows on an SSD and Linux on a separate HD.

I can't for the life of me, get grub to see or boot both.

Currently in Ubuntu only mode.

If I choose the Windows HD in BIOS I get to a grub shell, as it can't find a device...

Any help greatly appreciated.

---

### Post by merrem2 on 2018-11-21
Good news, after repairing the MBR on sdb and pointing it to sdb1 (not sdb2 labelled (Windows) boot-repair) windows booted when I forced the bios to start sdb.

Not sure if I've got grub managing a dual boot yet though.

---

### Post by merrem2 on 2018-11-21
Further progress, I can now boot into windows by default.

Bad news, ubuntu will no longer boot.

Dual booting is harder than i remember! :roll:

---

### Post by oldfred on 2018-11-21
You have Ubuntu in sda with UEFI boot and Windows in sdb with BIOS boot.
You can do that, but  will only be able to boot from UEFI boot menu, not grub.
UEFI & BIOS are not compatible, or once you start booting in one mode you cannot switch.
You may have to turn on/off UEFI or CSM/Legacy mode to boot in correct mode for which every install you want to boot. Most newer UEFI will boot in correct mode when you choose in UEFI boot menu.

Since two drives, you want to have Windows BIOS boot loader in MBR of Windows drive. You do not need grub in MBR of Ubuntu drive as it is booting thru the ESP - efi system partition(but not easy to erase and space not used for anything else, so we leave it).

If you really want grub to boot Windows you have to convert Ubuntu install to BIOS boot. You can do that just by reinstalling the grub-pc (BIOS) version of grub. 
Since drive is gpt and must be gpt, you will need a bios_grub partition for grub to correctly install to MBR of sda. It is 1 or 2MB unformatted with bios_grub flag.

Use Boot-Repair's advanced options or your Windows repair/recovery flash drive to restore a Windows boot loader to MBR of sdb. Do not run auto-fix with Boot-Repair, only advanced options, since you want different boot loaders in each drive.

Other alternative is to reinstall Windows in UEFI mode, since you must have a newer UEFI hardware system. How you boot install media UEFI or BIOS/CSM/Legacy is then how it installs.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by merrem2 on 2018-11-22
Would it be worth converting the Windows drive to UEFI?

Would that solve my issue?

---

### Post by oldfred on 2018-11-22
They just need to be in same boot mode, both BIOS or both UEFI.
But there are some advantages to UEFI and gpt partitioning.

Windows only boots in UEFI mode from gpt, which in effect erases drive. So you have to back up all your data before reinstalling. You cannot do an image backup of MBR install and restore to gpt drive as partitions are different.
Windows is a bit more difficult to reinstall, but it is up to you.

       How to Clean Install Windows 10 in UEFI mode
[URL="https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html"]https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html

      [/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 
    [URL="https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html"]
[/URL]

---

### Post by merrem2 on 2018-11-28
I've converted my MBR windows to GPT with WinPE & mbr2gpt.

Not data loss! AFAIK at least.

Now attempting to recover my ubuntu install. Boot-repair didn't seem to like the new config. 

I'm currently attempting a ubuntu reinstall, but it appears to be hanging on "detect file systems..."

---

### Post by oldfred on 2018-11-28
Ubuntu should have been just fine. This should of added a UEFI Windows to UEFI grub menu.
sudo update-grub

If still issues, post link to new Summary Report from Boot-Repair.

---

