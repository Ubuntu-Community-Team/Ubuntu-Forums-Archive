---
title: "fsck Dirty Bit Options"
date: 2020-01-10
forum: Installation &amp; Upgrades
---

### Post by Yogi2 on 2020-01-10
**MY COMPUTER**

 Model: Msi GL72 7QF
Processor: Intel i7-7700HQ; 2.8GH
 RAM: 16GB DDR4
GPU: nVidia GTX960M, Optimus enabled
SSD: 500GB, GPT UEFI
OS: Windows10 Insider Preview; Mageia 7; Ubuntu 18.04.3 LTS

Secure boot and fast boot are disabled.


[HR][/HR]
I'm trying to install Ubuntu 18.04.3 and am receiving an error message that Grub cannot install.  One of the things I did to troubleshoot was run *fsck *to examine the ESP partition.  This is the results:
```
root@msi:~# fsck /dev/sda2
fsck from util-linux 2.31.1
fsck.fat 4.1 (2017-01-24)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 2
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/sda2: 725 files, 16131/76646 clusters
root@msi:~# 
```

I chose not to fix anything because I don't know what fsck is telling me.  What is a dirty bit and why should I care about it?  Also, since I'm having trouble installing Ubuntu, do I really want to rely on the backup boot sector?  Any insights would be greatly appreciated.

---

### Post by TheFu on 2020-01-10
Windows didn't close all the partitions correctly, so Linux will not touch them.  I think there are 2 settings inside Windows that need to be changed to ensure when you shutdown, that is actually closes all the file systems.  Fast start or fast boot ... something like that (microsoft changes the names).  You'll want to do some reading on installing and running dual-boot Windows + Linux.  It is a common issue.  Also, disable hibernation in Windows.

BTW, using fsck on a fat32 partition isn't a good idea.

---

### Post by Yogi2 on 2020-01-10
**TheFu-** Thank you for your suggestions.  Hibernation, secure boot, and fast boot are disabled in BIOS and in Windows.  The problem I'm experiencing is with Ubuntu, not with Windows.  The Ubuntu installer, Ubiquity, gives an error message saying it cannot install grub.  I have another Linux distro, Mageia, already installed and working properly.  In fact I can boot up Ubuntu if I use reFINd instead of the missing Grub.  

I am not very familiar with Linux and it's diagnostic tools.  What can you suggest I use to verify the integrity of the ESP partition?

---

### Post by SeijiSensei on 2020-01-10
I would choose to use Windows chkdsk over fsck on FAT/NTFS partitions.

---

### Post by TheFu on 2020-01-10
The "dirty bit" on a file system means it wasn't properly closed.  That means it is 99% likely a Windows problem, not Linux.

However, 
* I don't dual boot.
* I don't run 18.04 or newer.

When you boot from a "Try Ubuntu" flash drive, are the same issues seen?  Can it open all the partitions?

---

### Post by oldfred on 2020-01-10
You can run fsck.vfat or dosfsck on FAT32. Or use Windows chkdsk.
Linux does not have any good tools to repair NTFS, ntfsfix really just turns on the chkdsk flag, so Windows will fix it.
fsck, e2fsck is only for ext2, ext3, ext4 family of formats.

dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, change sda1 example to your FAT32 partition(s).
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

man dosfsck
> NAME
       fsck.fat - check and repair MS-DOS filesystems



---

### Post by Yogi2 on 2020-01-10
Using [COLOR=#006400]**fsck -a /dev/sda2**[/COLOR] cleared the dirty bit.
Using Windoiws [COLOR=#006400]**chkdsk **[/COLOR]returned zero errors.
Installing Ubuntu 18.04 fails with the same error as previously noted.  
I have to consider this (dirty bit) problem solved.  However, I'll likely open another thread to try and solve the problem with installation errors.

---

