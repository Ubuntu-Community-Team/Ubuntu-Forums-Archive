---
title: "Partitioning issues"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by hare05 on 2011-12-19
Hi.

I'm trying to install Ubuntu 11.10 on my new disk, my system layout is as follows (left to right in GParted):

[INDENT]2.0TB (SATA )(new): [1.78TB Ubuntu] [4GB Swap] [30GB Unallocated] 
[/INDENT][INDENT]400GB (1) (SATA): [360GB Media] [40GB Windows]
[/INDENT][INDENT]400GB (2) (IDE): [All Media]

[/INDENT]I intended to install Ubuntu at the end of the 2.0TB drive, in the 30GB partition and migrate Windows across to take up the rest of the space.

I installed Ubuntu to the 30GB space, but it wouldn't boot.

I used the LiveCD again, and was given an option to repair the installation. I chose that.

Ubuntu booted this time, but now takes up nearly the entire drive. The 30GB drive it was MEANT to install to is the only unallocated space left. Windows is now no longer able to boot.

GParted will not let me reduce the size of or move the Ubuntu drive. 

Can someone help me figure out how exactly this happened?

---

### Post by BC59 on 2011-12-19
Open a terminal and post the result of those 2 commands please:

```
sudo parted /dev/sda print

sudo fdisk -l
```

---

### Post by hare05 on 2011-12-19
sudo parted /dev/sda print

Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 3      1018kB  1961GB  1961GB  ext4
 4      1961GB  1965GB  4295MB  linux-swap(v1)



sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3abb3aba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            2048   697156739   348577346    7  HPFS/NTFS/exFAT
/dev/sdb3       697156740   781401599    42122430    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0eb5ab4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   604880064   302440001    7  HPFS/NTFS/exFAT
/dev/sdc2       604880896   646823935    20971520    f  W95 Ext'd (LBA)
/dev/sdc3       646823936   718501887    35838976    7  HPFS/NTFS/exFAT
/dev/sdc4       718503936   781418495    31457280    7  HPFS/NTFS/exFAT

---

### Post by oldfred on 2011-12-19
Ubuntu defaults to gpt(GUID) for larger drives. It is only required for drives over 2TiB or about 2.2TB. But windows will only boot from gpt partitioning if you boot with UEFI. If you want to boot with Windows on the large drive you need to partition in advance with MBR(msdos)), and not let the auto installer control it. You should also create a shared NTFS partition for any data you may want in both systems (I have Firefox & Thunderbird profiles in a shared) so you do not have to write directly into the Windows system partition (c:).

I use gpt on my SSD & one small drive to learn about it, but boot with BIOS not UEFI. I have MBR on my XP drive and my larger (640GB) drive.

Grub/Ubuntu used to have a bug that it would not boot from very large root partitions like yours, but you are able to boot? Maybe they have fixed it. Or maybe that is why the gpt vs. msdos on large drives?? I would keep / (root) partition smaller in your new install.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by hare05 on 2011-12-19
My intent was to create a 30GB Ubuntu partition at the end of the drive, as an emergency / diagnostic / partitioning system so I can access windows files should windows fail. The rest of the 2TB drive was just going to be C: drive. 

I've had a lot of trouble with using small OS partitions and grouping media files, etc onto separate partitions as my family also make use of the computer and tend to save crap all over the place on the C: drive.

Ubuntu can access the windows C: drive without problems. I see no reason to create a shared drive as my main other reason to use a Linux partition is to avoid all the distractions (games / bookmarks) I have in Windows :D

I'm going to reinstall, but this time I think I'll install Windows directly over Ubuntu (the 1.78TB partition) and then install Ubuntu again from within Windows into the 30GB unallocated space.

Just to clarify again... 

Ubuntu boot partition should have '/' chosen in the menu, and a small 'swap' partition? I mistakenly chose /boot for my Ubuntu partition the first time then...

---

### Post by oldfred on 2011-12-19
Most desktops do not need a separate /boot partition. Only those with RAID, LVM or special formats that grub cannot read. Usually servers.

Reading from the Windows partition is ok, often best to set it to read only and permanently mount it in fstab, that way to avoid issues.

Windows will not correctly remove the gpt info and will create problems. The newer gpt also has a backup of the partition table and Windows only removes the primary. Then other software sees the backup and thinks it is gpt when Windows has added MBR partitions.

You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

The gdisk is in the repositories and you can download it, or download the newer version from the rodsbooks site.

---

