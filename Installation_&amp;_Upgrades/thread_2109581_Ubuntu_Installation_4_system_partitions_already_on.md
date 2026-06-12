---
title: "Ubuntu Installation 4 system partitions already on machine"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by codeomnitrix on 2013-01-28
Hi,

I want to install Ubuntu 12.04 LTS on my Dell Inspirion machine but the issue is I can't go for the logical or extended partition as I am having the following partitions on my machine:


[LIST]
[*]EFI System Partition (500MB)  
[*]OEM Partition (400MB) 
[*]Recovery Partition (500MB) 
[*]Recovery Partition (7.87GB) 
[*]Windows8 Partition (105GB) 
[*]Other 1 (255GB) 
[*]Other 2 (100GB)
[/LIST]


Please suggest how to install ubuntu 12.04 LTS on the machine as it says the machine should have only four primary partitions and rest all it identifies as raw partitions

---

### Post by Mark Phelps on 2013-01-29
The four partition limit is for MBR formatted disks; yours is GPT.

Your PC uses the new UEFI BIOS -- something I stay away from, so any instructions you follow need to be SPECIFICALLY for UEFI BIOS machines. IF you follow the wrong instructions, you risk trashing the PC.  My advise is to wait for "oldfred" to respond -- he seems to know a lot about UEFI and dual-booting.

I would do TWO things BEFORE you attempt the install:
1) Create Win8 Repair CD -- do that using the Backup feature.  This will give you a way to recover your Win8 boot loader, should you need to.
2) Install the FREE version of Macrium Reflect and use that to do a backup of the Win8 setup to an external drive.

THEN, if you still want to dual boot, use ONLY the Win8 Disk Management utility to shrink Win8 to make room for Ubuntu.  Do NOT use the Ubuntu installer or GParted to do that -- using those risks corrupting the Win8 OS and rendering it unbootable.

---

### Post by oscarivera9 on 2013-01-29
> **codeomnitrix said:**
> Hi,

I want to install Ubuntu 12.04 LTS on my Dell Inspirion machine but the issue is I can't go for the logical or extended partition as I am having the following partitions on my machine:


[LIST]
[*]EFI System Partition (500MB)
[*]OEM Partition (400MB)
[*]Recovery Partition (500MB)
[*]Recovery Partition (7.87GB)
[*]Windows8 Partition (105GB)
[*]Other 1 (255GB)
[*]Other 2 (100GB)
[/LIST]


Please suggest how to install ubuntu 12.04 LTS on the machine as it says the machine should have only four primary partitions and rest all it identifies as raw partitions

I agree with Mark Phelps, wait for oldfred to help out, he's very knowledgeable with this sort of thing.   Also, you **ARE** using GPT which lets you have as many partitions as you need.  The four partition limit only applies to MBR.  If you think about it, you already have 5-7 partitions.
However, I do have one question:  What are the Other1 & Other2 partitions?
 I have a UEFI/GPT system and to me it seems like you're pretty much ready to proceed with installation.  The reason I say so is that for an installation in UEFI you need a UEFI partition which your PC already has.  It would definitely help to know what's installed in those two partitions I mentioned.

---

### Post by oldfred on 2013-01-29
I would suggest 12.10 as that has grub2 2.00 that also includes secure boot. If you want 12.04 you can wait a couple of weeks. Grub2 2.00 will be in the next point release of 12.04 but that has been delayed until Mid-Feb.

Follow the backup & create a Windows repairCD suggestions by Mark Phelps before doing anything. And use Windows to shrink the main Windows partition to make room for Ubuntu. And reboot several times into Windows.

Each vendor has slightly different UEFI implementations. Some work without much issue, some have issues and some are extremely difficult to try to dual boot.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Other Dell users who did get installed.
       Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)
   
You will also need Boot-Repair. Grub has a but and does not create correct chain load entries to Windows efi. But Boot-Repair makes it easy to fix or you can use the manual workaround in the bug. 

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Once you have backed up everything, created repair/recovery disks and reviewed instructions, come back with any additional questions. Good preparation reduces installation issues and simplifies corrections or fixes.

---

