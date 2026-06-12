---
title: "Difficulty resizing windows partition to make a boot partition with large disk"
date: 2016-07-20
forum: Installation &amp; Upgrades
---

### Post by markmcc2 on 2016-07-20
I have a 2 TB hard drive and installed Ubuntu as a second operating system on my computer. I made the Ubuntu partition the final 300 GB on the drive. When I restarted, I got an error "attempt to read or write outside of disk 'hd0'" and neither operating system will boot. Googling, I learned this can happen if grub too far from the start of the disk. (Side note- it's crazy to me that the Ubuntu installer doesn't check the disk size and give a warning and/or automatically perform a workaround). Then I found these instructions on how to Install Ubuntu on a large disk ([https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)). First I tried boot-repair, checking the 'out of disk' option, but it still wouldn't boot. The final option is to create a boot partition at the start of the hard drive. BUT the problem is that my Windows partition is at the start of the hard drive. I read online that I should not use gparted to move the windows partition (shifting it from the left, rather than resizing from the right). Trouble is, I do not have a Windows boot CD (just got a computer with an image) and so I cannot boot into Windows and use the Windows partition tool. What can I do? Am I even on the right track with my attempted solution?

---

### Post by oldfred on 2016-07-20
Have not seen that type of error with UEFI & gpt systems.

Post this from Ubuntu or Ubuntu live installer:
sudo parted -l
sudo gdisk -l /dev/sda

---

### Post by markmcc2 on 2016-07-20
My BIOS is A07. I believe this is legacy, not UEFI. And the system is MBR, not GPT. Could this be an issue?

---

### Post by oldfred on 2016-07-20
Post the partition info.

The only issue with large drives has been old BIOS. Like over 10 years where BIOS was designed for IDE/PATA drives that were 120GB or less. Some newer systems booting from large USB drives have similar issue.

---

### Post by markmcc2 on 2016-07-20
I hope I am providing the information you are requesting. From sudo parted -l, I get:

Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  12.6GB  12.6GB  primary   ntfs            boot
 3      12.6GB  1594GB  1581GB  primary   ntfs
 4      1594GB  2000GB  407GB   extended
 5      1594GB  1932GB  338GB   logical   ext4
 6      1932GB  2000GB  68.6GB  logical   linux-swap(v1)


Model: SMI USB DISK (scsi)
Disk /dev/sdb: 4028MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4028MB  4027MB  primary  fat32        boot, lba

From sudo gdisk -l/dev/sda, I get:

GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Exact type match not found for type code DE00; assigning type code for
'Linux filesystem'
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): D61CB083-9E80-4BAA-8866-2058D70CC615
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 8-sector boundaries
Total free space is 4068 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63           80324   39.2 MiB    8300  Linux filesystem
   2           81920        24686591   11.7 GiB    0700  Microsoft basic data
   3        24686592      3113006850   1.4 TiB     0700  Microsoft basic data
   5      3113007104      3772964863   314.7 GiB   8300  Linux filesystem
   6      3772966912      3907028991   63.9 GiB    8200  Linux swap

The computer is less than a year old. Dell.

---

### Post by markmcc2 on 2016-07-20
More background, if this is useful, I originally installed Ubuntu dual boot on this machine about 9 months ago. Used it without issue until this weekend. This weekend, I restarted (hadn't done anything in particular) and this problem occurred. I ran a Dell system diagnostic and on a call with their support, they said it was a hardware issue and replaced the hard drive. So then I started over with this new hard drive (which had Windows installed) and immediately reinstalled the dual boot. This time the problem occurred after the first reboot.

---

### Post by oldfred on 2016-07-21
I am a bit surprised that a year old system is BIOS/MBR. New systems all are UEFI/gpt. And 3TB drives have to be gpt.

But you have a standard old configuration of BIOS with MBR(msdos) partitioning.

What model Dell? Do you have newest BIOS from Dell for that system?
Did you try restoring a Windows boot loader to MBR and directly booting Windows before calling Dell?

My Dell SFF wanted me to make a Dell backup, a Windows backup. I also made a full backup and a recovery flash drive. Lots of flash drives & DVDs, but then can easily repair or restore system. Of course then it wanted to upgrade from Windows 8 to Windows 10. And I am having issues getting rid of the Dell on line backup nag screens.

Do you have drive set for AHCI, not RAID nor IDE in BIOS?

---

### Post by markmcc2 on 2016-07-22
I have successfully been able to install and set up dual boot on the machine. Thank you very much for the helpful comments and questions. They gave me some good clues to follow up on. I learned a lot from this!
 
Here are the steps that I followed. This resulted in a working dual boot installation. Prior to this, if you turned on the computer, it gave a disk read error and could not boot into anything (it was possible to boot off live disks and BIOS could be accessed at startup through F12). (1) From a flash drive, updated the BIOS from A07 to the latest version, A13. (2) Downloaded a Windows iso and formatted onto a flash drive. (3) Reinstalled Windows from the flash drive. (4) When reinstalling Windows, I deleted all partitions except a very small protected partition that came preloaded on the drive. That is, I deleted: the old Ubuntu partition, the old Windows partition, and a “recovery” partition at the start of the drive that came loaded onto the drive when it was shipped by Dell. (5) Within Windows, I partitioned the drive to leave 500 GB at the end for Ubuntu. (6) Booted from an Ubuntu installation flash drive and installed Ubuntu into the unallocated 500 GB.
 
I deleted the Dell recovery partition because I read that dual boots may have problems if Windows isn’t installed at the very start of the drive. I also read that it is better to do the drive partition from within Windows, and then install into the unallocated space, rather than to let Ubuntu shrink the Windows partition during installation. I updated to the newest BIOS because who knows, couldn’t hurt.
 
Prior to this weekend, the dual boot had worked fine since I set it up 9 months ago. I know that right before the problem started, the system (from within Windows) had downloaded some kind of BIOS update (because it had given me a message saying so), and because this happened right before the system stopped booting, I infer this is what triggered the issue.

---

### Post by markmcc2 on 2016-09-30
Here is a final update. This should give some closure on the issue, hopefully. 

After my above post on July 22, the problem reoccurred after a few days. Then, I gave up on dual boot, wiped the drive, and attempted a single boot. The computer booted ok for a week, and then the problem reoccurred!

After much more pulling of hair, here is how the problem was solved. The hard drive itself was not the problem, because the hard drive had already been replaced (which temporarily had fixed the problem). Next, Dell support replaced the actual physical wire that connected the hard drive to the motherboard. That immediately resolved the issue, and it has now been a few months and I have not had any reoccurrence of the problem. It seems that dual boot was a red herring- the problem occurred even when running single boot. the problem was solely a hardware problem, a faulty wire! This was peculiar because the data on the hard drive could be written/read if you booted the OS from a flash drive. I don't know enough to understand exactly how this all played out within the BIOS, hardware, etc. But I can say that, empirically, replacing that darn wire fixed the problem, while nothing else did.

---

