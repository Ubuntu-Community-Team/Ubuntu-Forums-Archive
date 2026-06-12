---
title: "Dual Booting Windows 8.1 And Ubuntu 14.04"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by nlane515 on 2014-04-17
Alright guys so here's the issue. A while back I deleted my Windows 8.1 partition and was fine. But then I wanted to do some gaming, so I reinstalled Windows 8.1 over everything. I shrunk my Windows partition while I was still in Windows, but when I go install Ubuntu 14.04, it doesn't see Windows partitions, or the partitions I created for it, instead it just sees blank space, along with the boot loader for Windows. I already have fast boot off, but I can't turn secure boot or UEFI off or else I can't boot Windows. SO, what do you guys suggest I do?

---

### Post by oldfred on 2014-04-17
You should be able to turn secure boot off in UEFI menu. And Windows should still boot.
But you must have fast boot off. Windows may keep turning it on when ever you do fixes in Windows.

Did you reinstall Windows in UEFI or BIOS boot mode?
If you converted to BIOS, it also converted drive from gpt to MBR(msdos) but does not do it correctly and leaves backup gpt partition table. Then Linux tools cannot tell if you want MBR or gpt. But we need to be sure you do not want gpt, before erasing backup gpt table.

From live installer post this:
sudo parted -l
sudo fdisk -lu

fdisk does not work on gpt drives but does for MBR drives.

---

### Post by nlane515 on 2014-04-17
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd3a42dd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   874860543   437070848    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4015 MB, 4015718400 bytes
80 heads, 15 sectors/track, 6536 cylinders, total 7843200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         256     7843199     3921472    b  W95 FAT32
ubuntu@ubuntu:~$ 



ubuntu@ubuntu:~$ [http://ubuntuforums.org/showthread.php?t=2217560&p=12991131#post12991131](http://ubuntuforums.org/showthread.php?t=2217560&p=12991131#post12991131)
[1] 4008
ubuntu@ubuntu:~$ bash: [http://ubuntuforums.org/showthread.php?t=2217560:](http://ubuntuforums.org/showthread.php?t=2217560:) No suchubuntu@ubuntu:~$  sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?

---

### Post by nlane515 on 2014-04-17
[http://imgur.com/XWKduBG](http://imgur.com/XWKduBG)

---

### Post by nlane515 on 2014-04-17
[http://imgur.com/7gBI0VO](http://imgur.com/7gBI0VO)

---

### Post by oldfred on 2014-04-17
You reinstalled Windows in BIOS boot mode with MBR partitioning. You only have two NTFS partitions. If you had an efi partition and a msftres partition then you would have an UEFI install.

But Windows does not correctly convert fully to MBR. It leave the backup gpt partition table which is one of gpt's advantages that it has a backup.
Then with MBR partitions and a backup gpt partition table Linux tools do not know what you have gpt or MBR or what you want.

If you just want MBR, you need to remove the backup gpt partition table. But then be sure to boot everything in BIOS mode and do not boot anything in UEFI mode. How you boot an installer or repair drive is how it installs.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

