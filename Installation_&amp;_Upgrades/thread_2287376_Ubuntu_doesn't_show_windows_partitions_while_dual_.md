---
title: "Ubuntu doesn't show windows partitions while dual booting"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by pranish on 2015-07-18
i have windows 8.1 and I want to dual boot it with ubuntu gnome 14. I have seperated a disk with 50 GB space. I formatted it with NTFS and FAT 32 and also tried to unalocate the space for it. But non of the method worked. The ubuntu installation shows the hard disk as a full 500 GB hard disk. No windows partitions are shown. Please help

---

### Post by tokyobadger on 2015-07-19
Use the ubuntu install media to enter a live session, open the terminal, type sudo fdisk -l (password is ubuntu), copy the output from the terminal, open the browser and reply to this thread pasting the output in code tags

---

### Post by pranish on 2015-07-19
Okay I did that and here is the screen shot of it. Now when I tried to install ubuntu it showed the windows partitions and windows os installed. But I dont know how it happenned. Please can you explain? 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4cf6e5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   210450431   104865792    7  HPFS/NTFS/exFAT
/dev/sda3       584456832   871898752   143720960+   7  HPFS/NTFS/exFAT
/dev/sda4       210451505   584456828   187002662    f  W95 Ext'd (LBA)
/dev/sda5       210451568   584456828   187002630+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order

Disk /dev/sdb: 15.5 GB, 15504900096 bytes
255 heads, 63 sectors/track, 1885 cylinders, total 30283008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    30281727    15139840    c  W95 FAT32 (LBA)


```

---

### Post by tokyobadger on 2015-07-19
You have two hard drives /dev/sda and /dev/sdb. /dev/sda looks like your windows install (NTFS file system) - what's on /dev/sdb?

---

### Post by yancek on 2015-07-19
Did you install windows 8.1 or was it pre-installed?  You don't seem to have an EFI partition which would indicate windows installed in BIOS mode using MBR.  If that is the case, you already have four primary partitions in use taking up the entire drive so there is no space on which to install Ubuntu.  You also will NOT be able to get a working Ubuntu/Linux system on a partition formatted ntfs.  You do not have any Linux partitions.

---

### Post by oldfred on 2015-07-19
The sda4 is an extended partition with sda5 formatted as NTFS. Ubuntu will not install to a NTFS partition. If partitioning in advance use gparted to change sda5 to ext4 format and maybe shrink a bit to make room for a 2GB swap partition. Or just delete NTFS sda5 partition & Ubuntu should install into unallocated (not formatted) space.

But Windows 8 even in BIOS mode still has the fast startup setting. Which is really always on hibernation. And Linux will not mount NTFS needing chkdsk or hibernated, so then Linux cannot see that you have a Windows install.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by pranish on 2015-07-19
sdb is the usb stick

---

### Post by pranish on 2015-07-19
I installed the windows partition. Well I also thought the problem is with windows loader partition. Whats a system reserved partition?  Okay I have listed the things which I did previously in my laptop.1. Once I had installed the windows in partition other than drive C:. So now I have 2 primary partitions.2. I tried to delete "system reserved" drive (and I think it was deleted). But the current windows is installed afterwards.

---

### Post by pranish on 2015-07-19
You mean to say I have to create an "unalocated space" to install linux? I tried it previously while trying to install linux mint. I shutdown windows completely using "shutdown -s" command and then ran linux mint installation using a usb stick. When I tried to open the disk drives, it said cannot access the drive; even though I had shutdown windows properly. I dont know how but this time mint showed the windows partitions, I guess because I had an extended partition. And I chose the unalocated space to install mint but "continue" button was disabled when I chose the unalocated partition. I couldn't figure out whats wrong

---

### Post by oldfred on 2015-07-19
The 100MB system partition with BIOS is where Windows has its boot files. You should not normally delete that partition as then you cannot boot. IF you have copied bootmgr & BCD folder to c: drive then you can still boot, but then also have to move boot flag (active partition in Windows) to the Windows main install or c: drive. 
If that is what you deleted and you have no backups it is difficult to recover. As there are no copies of boot files anywhere else.

---

