---
title: "Problem when installing 12.04 on Windows 8.1 PC - grub rescue"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by monstrous behaviour on 2014-02-02
My dad's PC was having problems.  I think it was a mistake to  get Windows 8.1 installed in the first place, to be honest.  It's way  too fussy.
  Anyway, he was about to wipe the entire thing, and I suggested having a look at Ubuntu.
  I did the following:  
  tried to install via download from Firefox.....but his PC was so  flaky I couldn't be sure what was going on at times.  Lots of pop ups  etc. despite adblock being installed.
  I created an Ubuntu trial DVD and ran that.  he liked the look of it, so from within that I installed 12.04.  
  When it restarted I got a grub rescue prompt.  I have literally no idea what to do next.
  I had hoped to have a dual boot option at start-up, and then from  Ubuntu was hoping to be able to move files from the Windows partition.  
  I'd be grateful for any advice.
  Cheers
  Steve

---

### Post by fantab on 2014-02-02
First of all, if you like the look of Windows7 then check out [Classic Shell]("http://classicshell.net/"). 

Tell us about your PC... its hardware details like UEFI, RAM, Graphics card etc... brand and model.

Post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```
booting from Ubuntu DVD.

---

### Post by monstrous behaviour on 2014-02-02
Hi - I'll have to pop over to his house again.  No idea of the PC and it's spec.  Will report back asap.  Thanks for responding.

---

### Post by monstrous behaviour on 2014-02-03
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  370MB  370MB   primary   ntfs         boot
 3      370MB   484GB  484GB   primary   ntfs
 4      484GB   493GB  8678MB  primary   ntfs
 2      493GB   500GB  7043MB  extended
 5      493GB   500GB  7041MB  logical   fat32


Model: SanDisk Cruzer (scsi)
Disk /dev/sdc: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      19.5kB  4014MB  4014MB  primary  fat32


Model: Generic STORAGE DEVICE (scsi)
Disk /dev/sdd: 2033MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      127kB  2031MB  2031MB  primary  fat16


Model: Seagate Expansion Desk (scsi)
Disk /dev/sdi: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1006GB  1006GB  primary   ntfs
 2      1006GB  2000GB  995GB   extended
 5      1006GB  1997GB  991GB   logical   ext4
 6      1997GB  2000GB  3706MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by monstrous behaviour on 2014-02-03
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb1c44ea9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      722924      361431    7  HPFS/NTFS/exFAT
/dev/sda2       963016425   976773167     6878371+   5  Extended
/dev/sda3          722925   946067849   472672462+   7  HPFS/NTFS/exFAT
/dev/sda4       946067850   963016424     8474287+   7  HPFS/NTFS/exFAT
/dev/sda5       963016488   976768064     6875788+  bc  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2c49399c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              38     7839719     3919841    b  W95 FAT32

Disk /dev/sdd: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x45242cb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1             249     3967487     1983619+   6  FAT16

Disk /dev/sdi: 2000.4 GB, 2000398933504 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfc2d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1            2048  1964583671   982290812    7  HPFS/NTFS/exFAT
/dev/sdi2      1964584958  3907028991   971222017    5  Extended
/dev/sdi5      1964584960  3899789311   967602176   83  Linux
/dev/sdi6      3899791360  3907028991     3618816   82  Linux swap / Solaris

---

### Post by monstrous behaviour on 2014-02-03
hope someone can help

---

### Post by monstrous behaviour on 2014-02-03
I should have said that when the PC is switched on we get the following:

error: no such device: 4376b2fc-07c9-4e08-bc3c-b8e41dfd8888.
grub rescue>

---

### Post by fantab on 2014-02-03
Post the output of:
```
sudo blkid
```

That error is related to UUID of a partition.

---

### Post by monstrous behaviour on 2014-02-03
OK - will do.  That'll be tomorrow's exciting installment.  :)

---

### Post by ubfan1 on 2014-02-03
Another item to check:  grub and the BIOS sometimes enumerate the disks differently.  This can result in the /boot/grub/grub.cfg file using the "wrong" devices in lines using hd8,msdos5 or ahci8,msdos5.  Just after poweron, type the function key, or ESC, or whatever your machine uses to give you a choice of devices to boot.  See where in the list your linux disk appears (looks like sdi above, so I'd expect your grub.cfg to use hd8 (disks start at 0)).  If the disk is not in the nineth from the top position, there is a disagreement on which device it is.  Count the position, subtract one, and from the live media, edit the hard disk's copy of grub.cfg and correct the hd8 s to hx (whatever you found).  Then try booting again.  Typical symptom of this mismatch is getting a purple screen (on 13.10), and nothing else, with no virtual terminals or any other input working.  The fix needs applying each time you update grub.  MIght be a way using drive maps to fix, but I don't recall.

---

