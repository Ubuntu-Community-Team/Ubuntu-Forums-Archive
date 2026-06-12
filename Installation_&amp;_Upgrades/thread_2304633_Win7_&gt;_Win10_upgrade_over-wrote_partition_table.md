---
title: "Win7 &gt; Win10 upgrade over-wrote partition table on multi-boot box"
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2015-11-28
Multi-boot = Ubuntu 14.04, Ubuntu Server, Win Vista, OpenSolaris, Win7 > Win10 (transitional).

Re: upgrade from Win7 to Win10 over-wrote 1st disk partition table, corrupted grub. Boots to unrecognised filesystem, grub rescue.

Output of blkid
```

ubuntu-gnome@ubuntu-gnome:~$ sudo blkid
/dev/sda1: LABEL="Mikes_1TB" UUID="40E0BF86E0BF80A8" TYPE="ntfs" PARTUUID="f0bf1b18-01"
/dev/sda2: UUID="8E469CB9469CA40D" TYPE="ntfs" PARTUUID="f0bf1b18-02"
/dev/sda3: UUID="e8e5733f-6875-491b-b5cc-21d6aac83f78" TYPE="ext4" PARTUUID="f0bf1b18-03"
/dev/sda5: UUID="2013-11-13-15-19-56-00" LABEL="Peppermint Four" TYPE="iso9660" PTUUID="2183fe55" PTTYPE="dos" PARTUUID="f0bf1b18-05"
/dev/sdb1: LABEL="New Volume" UUID="5E463D56463D2FDF" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="b74dc0b2-b5fc-497e-8ef0-221638ddc87f"
/dev/sdc1: UUID="E85C16665C163034" TYPE="ntfs" PARTUUID="9f9e5343-01"
/dev/sdd1: UUID="fdf5c6ae-a958-43ac-b65b-373e87cb3340" TYPE="ext4" PARTUUID="ee386106-01"
/dev/sdd2: LABEL="DATA" UUID="FA78A3B378A36CD7" TYPE="ntfs" PARTUUID="ee386106-02"
/dev/sr0: UUID="2015-04-22-12-59-27-00" LABEL="Ubuntu-GNOME 15.04 amd64" TYPE="iso9660" PTUUID="544a81b0" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/sdd5: UUID="27dd0aa3-108e-42e4-aac5-35b1865c70d7" TYPE="swap" PARTUUID="ee386106-05"
/dev/sdc2: PTUUID="9f9e5343" PTTYPE="dos" PARTUUID="9f9e5343-02"
/dev/sdc6: PTUUID="9f9e5343" PTTYPE="dos"
/dev/sdc7: PTUUID="9f9e5343" PTTYPE="dos"

```

Output of fdisk -l
```

ubuntu-gnome@ubuntu-gnome:~$ sudo fdisk -l

Disk /dev/loop0: 965.8 MiB, 1012744192 bytes, 1978016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf0bf1b18

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1212419654 1212417607 578.1G  7 HPFS/NTFS/exFAT
/dev/sda2       1212420096 1213339647     919552   449M 27 Hidden NTFS WinRE
/dev/sda3       1213341255 1941471314  728130060 347.2G 83 Linux
/dev/sda4       1941471315 1953520064   12048750   5.8G  f W95 Ext'd (LBA)
/dev/sda5       1941471378 1953520064   12048687   5.8G 82 Linux swap / Solaris

Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B55CD551-461D-4042-A8DF-E7D49C3BCD43

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7814035455 7814033408  3.7T Microsoft basic data

Disk /dev/sdc: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9f9e5343

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1              63 157292414 157292352    75G  7 HPFS/NTFS/exFAT
/dev/sdc2  *    157292415 488397167 331104753 157.9G bf Solaris

Disk /dev/sdd: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xee386106

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdd1  *         2048 218945535 218943488 104.4G 83 Linux
/dev/sdd2       228653145 976768064 748114920 356.7G  7 HPFS/NTFS/exFAT
/dev/sdd3       218947582 228653055   9705474   4.6G  5 Extended
/dev/sdd5       218947584 228653055   9705472   4.6G 82 Linux swap / Solaris

Partition table entries are not in disk order.

```

Output of testdisk /list
```

ubuntu-gnome@ubuntu-gnome:~$ sudo testdisk /list
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Sector size:512
Model: ST31000528AS, S/N:6VP0D71J, FW:CC34

Disk /dev/sdb - 4000 GB / 3726 GiB - CHS 486401 255 63
Sector size:512
Model: ST4000DM000-1F2168, S/N:Z301FNCD, FW:CC54

Disk /dev/sdc - 250 GB / 232 GiB - CHS 30401 255 63
Sector size:512
Model: Hitachi HDT725025VLA380, S/N:VFL104R633ENXX, FW:V5DOA73A

Disk /dev/sdd - 500 GB / 465 GiB - CHS 60801 255 63
Sector size:512
Model: ST3500630A, S/N:5QG1D5A5, FW:3.AAE

Disk /dev/sr0 - 1061 MB / 1012 MiB - 518144 sectors (RO)
Sector size:2048
Model: ATAPI   DVD A  DH24AAL, FW:ZP5A

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition            Start        End    Size in sectors
 1 * HPFS - NTFS              0  32 33 75469 161 27 1212417607 [Mikes_1TB]
     NTFS, blocksize=4096
 2 P Windows RE(store)    75469 168 28 75526 229 31     919552
 3 P Linux                75527   0  1 120850 254 63  728130060
     ext4 blocksize=4096 Large file Sparse superblock
 4 E extended LBA         120851   0  1 121600 254 63   12048750
 5 L Linux Swap           120851   1  1 121600 254 63   12048687

Disk /dev/sdb - 4000 GB / 3726 GiB - CHS 486401 255 63
     Partition            Start        End    Size in sectors
 1 P MS Data                     2048 7814035455 7814033408 [Basic data partition] [New Volume]
     NTFS, blocksize=4096

Disk /dev/sdc - 250 GB / 232 GiB - CHS 30401 255 63
     Partition            Start        End    Size in sectors
 1 P HPFS - NTFS              0   1  1  9790 254 63  157292352
     NTFS, blocksize=4096
 2 * Solaris               9791   0  1 30401  80 63  331104753

Disk /dev/sdd - 500 GB / 465 GiB - CHS 60801 255 63
     Partition            Start        End    Size in sectors
 1 * Linux                    0  32 33 13628 185 61  218943488
     ext4 blocksize=4096 Large file Sparse superblock
 3 E extended             13628 218 29 14232 253 37    9705474
 5 L Linux Swap           13628 218 31 14232 253 37    9705472
     SWAP2 version 1, pagesize=4096
 2 P HPFS - NTFS          14233   0  1 60800 254 63  748114920 [DATA]
     NTFS, blocksize=4096

Disk /dev/sr0 - 1061 MB / 1012 MiB - 518144 sectors (RO)
     Partition            Start        End    Size in sectors
   P ISO                            0     518143     518144 [Ubuntu-GNOME 15.04 amd64]
     ISO9660 blocksize=2048

```

In Testdisk, intitial scan of sda
```

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0  32 33 75469 161 27 1212417607 [Mikes_1TB]
 2 P Windows RE(store)    75469 168 28 75526 229 31     919552
 3 P Linux                75527   0  1 120850 254 63  728130060
 4 E extended LBA         120851   0  1 121600 254 63   12048750
 5 L Linux Swap           120851   1  1 121600 254 63   12048687
 5 L Linux Swap           120851   1  1 121600 254 63   12048687


```

My plan was to use testdisk to repair partitions, reinstall grub, get my linux instances back ... continue with Win's upgrade.

I usually do not start a partition at 0, so see that as the not-smart upgrade over-writing my grub boot manager. My swap, in the extended/logical partitian is confused.

I'm always a bit wary of rushing into making partition changes without outside advice and an extra set of eyes...

EDIT: Note that this box does not boot a Boot Repair LiveCD. (That disk somehow clears the bios on this box) BIOS is set to legacy (not efi).

---

### Post by oldfred on 2015-11-28
Understand how Windows installs.
It requires a primary NTFS partition with the boot flag for its boot partition or all its boot files. And the boot partition must be on the drive set as default boot in BIOS. And newest version overwrites the BCD on the boot partition and will  add other versions to its new BCD.

Windows reinstalls also forget to write various Linux logical partitions. If any Linux partitions on same drive, you must backup partition table, use sfdisk to create text file of existing partitions.
Windows also may create a Boot partition on the BIOS boot drive if installing to a different drive. That has just overwritten whatever was there.

Best to only have one drive with Windows and only have that drive installed/plugged in when upgrading.

Mostly Vista, but still applies to all BIOS boot. Info on grub legacy is obsolete now.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by MAFoElffen on 2015-11-28
LOL. I understand. Win assumes that it is the only OS on a disk and likes to be the near sector 0. That has not changed. Other things you mentioned... well sort of.

Since Win Server 2008 came out, Win wants to default it's install in 2 partitions-- a primary OS boot partition (64-128GBs) and another partition. M$ calls it's primary boot partition, it's system partition, which contains all it's boot files, system files, etc. It tweaks the names on those just to be difficult. It's root partition cannot be lvm (dynamic or storage spaces), software raid, nor encrypted. It needs a pure system in a basic type partition to do it's bootup and translations. BUT ...

You can still install Win Desktop versions 8.0, 8.1, 10, Windows Servers 2008, 2008R2, 2012, 2012R2, 2016 (Tech Preview) as being installed into one primary partition. In this particularity instance, the Win primary partition is sda1 and it has links to the 4TB disk. I do this all the time on both virtual and hard hosts. If I do a (now) default install, I find I reorg extensions to a larger disk by extending the libraries to other partitions.

After analyzing the disk structure, it overwrote the MBR and corrupted the extended partition. The only logical partition in extended of that disk is the 14.04.03 linux swap.

What I did as a quick fix was to write a windows MBR to that disk, to let it finish the Win10 upgrade. Once Windows had finished what it "wants" to do, then I will go back, delete the corrupted logical swap partition and re-add it. It's just a swap, so no bad.

What I did, was the first 2 upgrades here went so smooth ... and I got over confident & complacent. I should have backed this box up to one of my servers.
 -- Which once it upgrades and gets it's new product key, then I might just do that. Back it up... and reinstall it clean. That box started as Vista and Ubuntu 8.04. It was a production dev box, so I always just upgraded it in place. Now iI retired that one to a gamer box (entertainment), and there are 2 newer production dev boxes.

But as such, remember my challenge is having Linux and Windows play nicely, together in the "same" world, seamless to the user. If I didn't have a work requirement for Win... Life would be so much simpler

Status-- Win 10 is @ 75% on the last leg of it's upgrade on that box. I can still see and access everything on that disk in ext4 from other instances of Linux, so see no problems. Will mark this as solved when I get there. 

This is a 2d Gen ASUS i5 board. Even though it is UEFI, it replaced an older legacy, so was a quick plug-n-play fix to get it back up for production. Had no choice at the time. Now, it's just finding spare time.

---

### Post by MAFoElffen on 2015-11-28
[SOLVED]
Like I said: (for non-efi disks)
Use testdisk to analyze the partition structure. Most of the time, when it fails, WIN10 will overwrite the mbr and mess with the logical partitions.
Repair the partitions
Use testdisk to write a boot mbr to disk... to let Win10 finish upgrading.

Reboot on LiveCD. Mount the Linux root partition.
Update the fstab with any new UUID's, if needed
Mount the other parts for a chroot. chroot into the linux installation.
Reinstall grub and update grub. On install of grub, it will warn that the previous mbr write had written micro-code to the mbr... (that was just an interim fix anyways)
Re-Boot into installed Linux instance and clean up.

---

