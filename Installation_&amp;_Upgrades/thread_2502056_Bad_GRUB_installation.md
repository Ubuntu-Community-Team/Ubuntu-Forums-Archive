---
title: "Bad GRUB installation"
date: 2024-10-31
forum: Installation &amp; Upgrades
---

### Post by piotrekzz on 2024-10-31
Hello Dears,

I've installed Ubuntu 24.04.1 LTS by booting from USB, creating partition on one of my SSD. Everything went OK but there is no option to go into Ubuntu when PC is booting. The only option is to boot from USB again. I've read that it is connected with GRUB file; I've tried to reinstall Ubuntu but now, there is no option to choose partition - only whole disk erase and instal...
I'm attaching report from Boot repair 
 [https://paste.ubuntu.com/p/2F2q2JKGf5/](https://paste.ubuntu.com/p/2F2q2JKGf5/)

  
Help please.
Piotrekzz

---

### Post by tea for one on 2024-10-31
Generally, when you have Windows 10/11 on one disk and Ubuntu 24.04 on a separate disk, there should be almost zero problems.
Your Ubuntu disk contains a huge ntfs partition (sdb2 845GB) at the beginning of disk sdb, hence the message as follows:-
[COLOR="#0000FF"]Line 285[/COLOR] - The boot files of [sdb3 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them etc

Also, please note this info:-
[COLOR="#0000FF"]Line 279[/COLOR] - The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode.

Does Windows boot successfully?
If Windows still boots OK, I would suggest that you rethink where you wish to keep ntfs partitions.
The foolproof way to install Ubuntu on a separate disk is to remove the Windows disk and only have the target disk accessible.

---

### Post by piotrekzz on 2024-11-04
Thank you for this answer very much!. I'm going to have windows on disk 0 and Ubuntu on disk 1 together with ntfs 845 GB partition. Is that possible or should i have to change file system on this big partition?

---

### Post by yancek on 2024-11-04
The comment in post 2 above shows you have a nearly 850GB ntfs filesystem partition at the "beginning" of the drive which is why you see the message on line 285 of boot repair.  You have an EFI install of windows on one drive showing the proper windows boot files there.  You have an EFI partition on the 2nd Ubuntu drive but no EFI boot files show on the EFI partition so if they are not there, it won't boot.  Also notice the message that when you ran boot repair, you did it in Legacy mode and you need to boot in UEFI mode to make any changes to or reinstall Grub.  Boot and select to boot from the UEFI menu.

If you want a partition on the Ubuntu drive to share with windows, you need a windows filesystem such as ntfs as a default windows can't read a Linux filesystem.  You can use some windows software like Disk Management to move the partition to the right toward the end of the disk and and then reinstall Ubuntu at the beginning of the disk.  If you have data on that windows partition, you might want to move it to another drive as modifying partitions always has the risk of data loss.

Before doing that you could do as suggested in boot repair and that is to boot in UEFI mode from the BIOS and reinstall Grub in EFI to the Ubuntu disk and see if it boots.

---

