---
title: "What to do if my EFI folder is empty?"
date: 2017-07-12
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2017-07-12
Inside the boot folder I have 2 subfolders: grub, and efi. 
However, the efi dir is empty! I suppose this is a problem.
Then, am I to create the missing ubuntu dir and the shimx64.efi file inside it?
If so, how?

I came to realize this while doing the usual bcdediting in Windows 10 to reconnect with the shimx64.efi file after using the Boot Repair Disk. Except bcdedit is failing to find such .efi file.

---

### Post by ubfan1 on 2017-07-12
Is your efi partition mounted at /boot/efi?  If not, then empty is what's expected.

---

### Post by yancek on 2017-07-12
EFI is on a separate partition of it's own and you should be able to determine which it is by running gparted (if installed) or with sudo parted -l.  THis partition is where you would see the various efi files.

---

### Post by oldfred on 2017-07-12
Post this:
cat /etc/fstab

If the ESP - efi system partition is mounted with umask=0077, then it is hidden.
I think they changed from defaults for security reasons, but I change mine and Boot-Repair auto changes it to defaults so it can edit the ESP.

---

### Post by javierdl on 2017-07-12
Right, I think I found it. It's a FAT32 partition, flagged "boot, esp", right? It's on sdb1.
And yes, there I found the missing shimx64.efi file.

---

### Post by javierdl on 2017-07-12
oldfred,
This is what I've got with your command:
```

aufs / aufs re 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0 
```

---

### Post by oldfred on 2017-07-12
That must be from live installer, not from your system.
You then need to mount your / partition whether sda1 or sdb1 or whatever partition it is

sudo parted -l
       sudo mount /dev/sdXY/mnt 
Where X is drive like a in  sda and Y is partition like 2 in  sda2

then 
cat /mnt/etc/fstab

---

### Post by javierdl on 2017-07-13
```

ubuntu@ubuntu:/mnt/sdb1$ sudo parted -l
Model: ATA Patriot Torch LE (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  473MB  472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   578MB  105MB   fat32        EFI system partition          boot, esp
 3      578MB   595MB  16.8MB               Microsoft reserved partition  msftres
 4      595MB   120GB  119GB   ntfs         Basic data partition          msftdata


Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name   Flags
 1      1049kB  538MB   537MB   fat32           EF     boot, esp
 2      538MB   301GB   300GB   ext4            Steam
 3      301GB   615GB   315GB   ext4                   msftdata
 4      615GB   992GB   377GB   ext4
 5      992GB   1000GB  8523MB  linux-swap(v1)         diag


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdd: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  32.0GB  32.0GB  fat32


```


But this is what I am getting trying to mount sdb1:

```

ubuntu@ubuntu:/$ sudo mount /dev/sdb1/mnt
mount: can't find /dev/sdb1/mnt in /etc/fstab

```

---

### Post by yancek on 2017-07-13
Put a space after sdb1:  sudo mount -t vfat /dev/sdb1 /mnt (the -t vfat is the filesystem type which you probably don't need).

---

### Post by hgfischer on 2017-11-13
I'm having the same problem from the subject of this topic, but in a different context.

I have a working PXE setup for Ubuntu with BIOS/legacy mode, and now I need to make it work with EFI, because of big partitions.

I added some changes to the preseed file, to create the free 1MB, then the EFI partition, etc. The installation works, and I can check the partitioning made by the setup and confirm that it looks perfect. However, after installation has finished, there is nothing inside /boot/efi, and the system does not boot up. I always end up in a EFI shell during the restart, and from checking there I also can confirm that the EFI partition is empty.

Does anyone have any clue why this happens? I haven't found any documentation about this.

---

