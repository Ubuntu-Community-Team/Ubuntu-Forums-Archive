---
title: "Fresh install of 20.04.1 has setup a FAT32 partition ?"
date: 2020-11-01
forum: Installation &amp; Upgrades
---

### Post by oygle on 2020-11-01
One computer has 19.10 installed and the partitions are as follows:

> 
$ sudo parted -l
[sudo] password for *********: 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  17.8GB  17.8GB  primary   ext4            boot
 2      17.8GB  1000GB  982GB   extended
 5      17.8GB  22.8GB  5000MB  logical   linux-swap(v1)
 6      22.8GB  1000GB  977GB   logical   ext4


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 62.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  62.1GB  62.1GB  primary  fat32


and the other computer has just had a fresh install of 20.04.1 and the installation has setup a FAT32 partition with a mount point of /boot/efi

> 
$ sudo parted -l
[sudo] password for **********: 
Model: ATA Hitachi HTS72755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32        boot
 2      539MB   500GB  500GB  extended
 5      539MB   500GB  500GB  logical   ext4


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 62.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  62.1GB  62.1GB  primary  fat32


If I try to enter the folder there is a message > Could not enter folder /boot/efi.

Can I safely change the first partition to become EXT4 and increase the size to (say) 20 Gb ? I also wanted to add a SWAP partition; currently it is seen as a 2Gb file on /dev/sda5

---

### Post by CatKiller on 2020-11-01
> **oygle said:**
> Can I safely change the first partition to become EXT4 and increase the size to (say) 20 Gb ? 

No. That's your [ESP](https://en.wikipedia.org/wiki/EFI_system_partition). It needs to be FAT. 

>  I also wanted to add a SWAP partition; currently it is seen as a 2Gb file on /dev/sda5

The default got changed to a swap file rather than a swap partition when they got as good. You can create a bigger swap file or create a swap partition if you're comfortable with that; it's fairly straightforward.

---

### Post by yancek on 2020-11-01
Your install on the computer with 19.10 is a Legacy/MBR install while the install with 20.04 is an EFI install,  The EFI install requires the FAT32 partition for the EFI files and needs to be mounted at /boot/efi and is accessible only by root, using sudo on Ubuntu.  Take a look at the link below which gives a brief explanation of Legacy/EFI.

[https://askubuntu.com/questions/993269/difference-between-legacy-bios-and-uefi](https://askubuntu.com/questions/993269/difference-between-legacy-bios-and-uefi)

---

### Post by Dennis N on 2020-11-01
Your partitions for 20.04 is what the Ubuntu installer does when you select the "erase and install" option with bios mode. The OS will still function normally.

Here is confirmation from a Ubuntu 20.04 VM install in BIOS mode:
```
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   21.5GB  20.9GB  extended
 5      539MB   21.5GB  20.9GB  logical   ext4

```
The first partition isn't serving any purpose in this bios install, even though it is mounted  at /boot/efi. You will find it is empty.
```
root@Tyana-vm:~# cd /boot/efi
root@Tyana-vm:/boot/efi# tree
.

0 directories, 0 files

```

With 20.10, users report the installer makes a GPT partition table with a bios type install when using the "erase and install" option.

---

### Post by oygle on 2020-11-02
> **CatKiller said:**
> No. That's your [ESP](https://en.wikipedia.org/wiki/EFI_system_partition). It needs to be FAT. 

I remember I did try to make the BIOS set to UEFI, however an error msg that it was experimental, so didn't select it. The laptop is quite old. So, the installation has defaulted to EUFI/UFI despite the fact the BIOS is set to "no UEFI". Interesting.

> **CatKiller said:**
> 
The default got changed to a swap file rather than a swap partition when they got as good. You can create a bigger swap file or create a swap partition if you're comfortable with that; it's fairly straightforward.

Thanks, yes I might just add a swap partition.

> **yancek said:**
> Your install on the computer with 19.10 is a Legacy/MBR install while the install with 20.04 is an EFI install,  The EFI install requires the FAT32 partition for the EFI files and needs to be mounted at /boot/efi and is accessible only by root, using sudo on Ubuntu.  Take a look at the link below which gives a brief explanation of Legacy/EFI.

[https://askubuntu.com/questions/993269/difference-between-legacy-bios-and-uefi](https://askubuntu.com/questions/993269/difference-between-legacy-bios-and-uefi)

Okay, thanks.

> **Dennis N said:**
> Your partitions for 20.04 is what the Ubuntu installer does when you select the "erase and install" option with bios mode. The OS will still function normally.

From memory it was just "Try" or "Install" but the Install option may have recognised the empty hard drive, so no erase needed ?

> **Dennis N said:**
> 
Here is confirmation from a Ubuntu 20.04 VM install in BIOS mode:
```
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   21.5GB  20.9GB  extended
 5      539MB   21.5GB  20.9GB  logical   ext4

```

Okay thanks, that is basically the same as the 20.04.1 I have.

> **Dennis N said:**
> 
The first partition isn't serving any purpose in this bios install, even though it is mounted  at /boot/efi. You will find it is empty.
```
root@Tyana-vm:~# cd /boot/efi
root@Tyana-vm:/boot/efi# tree
.

0 directories, 0 files

```

Same here ..

```
$ sudo tree  /boot/efi
/boot/efi

0 directories, 0 files

```

> **Dennis N said:**
> With 20.10, users report the installer makes a GPT partition table with a bios type install when using the "erase and install" option.

Okay, I may install 20.10 later. The only reason I went for 20.04.1 was the LTS component.

---

