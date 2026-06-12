---
title: "Windows 8 EFI Error After Ubuntu Install"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by jake21 on 2014-02-18
Hello,

Last night I installed Ubuntu along-side my Windows 8 install. I got the common error, "Unknown Command 'drivemap'" and the EFI error that everyone gets. x.x I tried running the recommended repair of Boot Repair but nothing really changed. :( Any help would be amazing! Here is my boot info --> [http://paste.ubuntu.com/6956289/](http://paste.ubuntu.com/6956289/)

---

### Post by Bucky Ball on 2014-02-18
Welcome. Can you get into the BIOS and set it to boot from the other drive, sdb, rather than sda? sda has no bootloader in the MBR. sdb has all the info you need to boot. Unsure how sda became sdb but perhaps it was intended like that. Win generally complains if not on sda so that might have something to do with your problem. 

If you're having no joy, try swapping the SATA cables over on the motherboard (presuming this is a desktop). Plug sdb where sda is and vice versa. If this is a laptop with one drive, then you have an external drive plugged in and that would be moving the drive allocations around. Unplug it and reboot if there is an external plugged in at boot.

---

### Post by oldfred on 2014-02-19
Your sda is configured with gpt partitioning and UEFI booting.
Your sdb is configured for BIOS booting with MBR(msdos) partitioning.
The only way you can boot either system is from UEFI menu as BIOS & UEFI are not compatible.

It looks like Boot-Repair ran its "buggy" UEFI rename which will never work with your configuration. The rename is required for those UEFI that vendor modifies to only boot Windows. But then you can only boot Windows from grub menu. But once you start to boot in BIOS mode to get grub menu, you cannot switch to UEFI mode to boot Windows.

Undo rename with Boot-Repair, so you can boot Windows directly from UEFI menu. 
       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Once you convert to UEFI with gpt partitioning, I suggest that all drives should be gpt and all installs UEFI based. But some do dual boot with one install UEFI and the other BIOS, but only from UEFI menu or one time boot key like f12 if you have that. Some UEFI require you to change settings from UEFI to BIOS in UEFI before you can boot a system in the other mode, others auto switch.

---

