---
title: "GRUB won't boot into WIn 8"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by M@s on 2012-11-10
I recently tried to install a dual-boot system. First I created a separate NTFS partition for Win 8, and installed it successfully. Then I installed Ubuntu 12.04 on another ext4 partition, and now the computer boots fine into Ubuntu. But when I select Win 8 in the GRUB boot menu, the screen turns black and the flashing underline appears for half of a second, then it returns to GRUB. 

These are the boot commands:

```
setparams 'Windows 8 (loader) (on /dev/sdd1)'

insmod part_msdos
insmod ntfs
set root='(hd3,msdos1)'
search --no-floppy --fs-uuid --set=root CA787A37787A21FD
drivemap -s (hd0) ${root}
chainloader +1
```

How to fix this?

---

### Post by grahammechanical on 2012-11-10
I cannot help you much but according to this

> set root='(hd3,msdos1)'

Grub is looking for Windows 8 on the third hard disk and in its first partition. Is this correct? Is windows 8 installed on the third hard disk? You do not mention having more than on hard disk.

Regards.

---

### Post by M@s on 2012-11-10
Yes, I have two other disks for storage. Don't know how to determine the disk order, but in the Disk Utility the system disk shows up as the third one. 

The system disk /dev/sdd is partitioned as following:

367 MB NTFS (Bootable) | 52 GB NTFS (Windows) | 68 GB ext4 (Ubuntu)

---

### Post by oldfred on 2012-11-10
If you have multiple drives, it may be best to see all the details. Run the BootInfo report.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by richaustin on 2012-11-10
use Boot Repair and then in Windows use EasyBCD available at [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)

---

### Post by M@s on 2012-11-10
Gonna try it out. Can I run Boot-Repair from the working Ubuntu installation or do I have to use a Live CD?

---

### Post by oldfred on 2012-11-10
You can download and run Boot-Repair from a working install. 

Part of Boot-Repair's BootInfo report is the bootinfoscript which is a separate script. I run that script as part of every backup so I have documentation on where every install is, what boot loader is in every MBR, and partition starts & sizes just in case I have to attempt to rebuild a drive.

---

### Post by M@s on 2012-11-11
Boot-Repair solved it all! Thank you!

---

