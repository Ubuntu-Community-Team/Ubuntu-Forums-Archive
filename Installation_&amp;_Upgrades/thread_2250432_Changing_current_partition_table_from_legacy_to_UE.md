---
title: "Changing current partition table from legacy to UEFI for a dual boot."
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by jinx748 on 2014-10-28
I have Ubuntu 14.04 installed on a 2 TB drive and windows installed on a 1 TB drive. I have been trying for days to get them to dual boot. After much reading, scouring the web and reinstalling windows trying to fix my problem I think my problem is that the Windows drive is not UEFI while the Linux drive does have a UEFI partition table. So While I can manually go into the Bios and change the boot order, each drive will boot fine on its own but when trying to dual boot from the grub menu while the UEFI drive is first in the bios the windows drive will not boot at all. Now I seem to be getting other issues after my last windows installation. But they all seem to be related. 

Is it possible to change the partition table to UEFI on the windows drive without having to reinstall windows? Also, if I do have to reinstall windows again and recreate the partition table on the 1TB drive I would make it aGPT partition table correct?

sudo parted -l
```
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   516GB   516GB   primary   ntfs
 3      516GB   992GB   476GB   extended
 5      516GB   992GB   476GB   logical   fat32
 4      992GB   1000GB  8634MB  primary   linux-swap(v1)


Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  538MB   537MB   fat32              boot
 2      538MB   794MB   256MB   ext2
 3      794MB   2000GB  2000GB


Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label             

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 1991GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1991GB  1991GB  ext4


Error: /dev/mapper/sdb3_crypt: unrecognised disk label 

```


Sudo fdisk -l
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x426ecf55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1007063039   503428096    7  HPFS/NTFS/exFAT
/dev/sda3      1007063040  1936660479   464798720    5  Extended
/dev/sda4      1936660480  1953523711     8431616   82  Linux swap / Solaris
/dev/sda5      1007065088  1936658431   464796672    b  W95 FAT32

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/mapper/sdb3_crypt: 1999.6 GB, 1999602974720 bytes
255 heads, 63 sectors/track, 243104 cylinders, total 3905474560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sdb3_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 1991.1 GB, 1991069663232 bytes
255 heads, 63 sectors/track, 242067 cylinders, total 3888807936 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 8531 MB, 8531214336 bytes
255 heads, 63 sectors/track, 1037 cylinders, total 16662528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
```


Here is what is in /ETC/Grub.d/40_Custom

```
menuentry "Windows 7 (loader)" {
insmod part_msdos
insmod ntfs
set root='(hd1,msdos1)'
chainloader +1
}
```

---

### Post by ubfan1 on 2014-10-28
You could more easily make the Ubuntu into a BIOS boot than the Windows into a UEFI boot I think.  Do you even have any Windows UEFI bootloaders?  If you can get the bootmgfw.efi (Windows bootloader), you could try to make a 300M FAT partition for EFI by chopping off a piece of one of the existing ones, then put the bootloader into /EFI/Microsoft/Boot/bootmgfw.efi (I think that right, from memory).  The grub custom file is for the old style grub, so you'd need the new grub-efi installed.  Then your Windows boot paragraph will use the /EFI/Microsoft/Boot/bootmgfw.efi instead of the "-1" in the chainloader.

---

### Post by fantab on 2014-10-28
[GPT has advantages]("https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT").
[Install Windows7 in UEFI mode]("http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"). To do this you will have to delete all the partition on Windows HDD or /dev/sda ... hope you have a good data backup.

---

