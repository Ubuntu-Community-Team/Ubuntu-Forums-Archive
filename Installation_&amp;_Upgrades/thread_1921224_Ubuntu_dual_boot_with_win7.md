---
title: "Ubuntu dual boot with win7"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by matkobrcko on 2012-02-06
I tried to install ubuntu 11.10 on separate partition but it cannot see my win 7 installation, it says no operating system detected. Can any one help pls???

---

### Post by oldfred on 2012-02-06
Welcome to the forums.

How many partitions do you have? And did you create more than 4 in Windows as then it converts to SFS or dynamic which does not work with anything but Windows and not even all the Windows repair tools work.

Post this from a terminal in Ubuntu LiveCD.

```
sudo fdisk -lu
```

---

### Post by matkobrcko on 2012-02-06
Ive got two primary partitions.(basic disk) Ill try that command thanks for that

---

### Post by matkobrcko on 2012-02-06
After running that command in terminal I got this


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89d7bd46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   488386559   244089856    7  HPFS/NTFS/exFAT
/dev/sda3       488386560   976771071   244192256    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312576704   156288321    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 16.1 GB, 16131293184 bytes
255 heads, 63 sectors/track, 1961 cylinders, total 31506432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    31503464    15751701    c  W95 FAT32 (LBA)

---

### Post by darkod on 2012-02-06
Is that a GPT leftover oldfred? It says gpt table detected but the partitions look like normal msdos type.

Fixparts?

---

### Post by oldfred on 2012-02-06
I agree with Darko, it looks like leftover gpt info from somewhere. gpt keeps a backup of the partition table and Windows only reformat the primary. Other software then sees the backup and gets confused. 

Fixparts will remove the backup.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partiton table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Windows 7 64 bit will only work on gpt if booting from UEFI. So if you have a BIOS based system it would install in MBR mode and delete the primary gpt partition table.

---

### Post by matkobrcko on 2012-02-08
Ok thanks Ill try it out.

---

### Post by matkobrcko on 2012-02-08
Yep Its sorted thanks a lot for help

---

