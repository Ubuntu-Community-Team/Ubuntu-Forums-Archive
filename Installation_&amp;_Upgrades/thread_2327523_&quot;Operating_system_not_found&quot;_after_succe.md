---
title: "&quot;Operating system not found&quot; after successful install Ubuntu 16.04"
date: 2016-06-11
forum: Installation &amp; Upgrades
---

### Post by francisco38 on 2016-06-11
Hi!

This is a Sony vaio VPCF1 with Windows 7 Home from factory, passed to Windows 8. After tried to install Windows 7 but not possible to install (recovery partition is lost), I tried with Ubuntu and I could install.
However when booting from HD it gives the ugly error "Operating system not found". However, with the USB live Ubuntu disk it recognizes the OS in the disk and allows me to boot the HD system.
I checked in the forum similar issues, but this is how far I could get alone.

Sudo parted -l gives:

```
Modelo: ATA TOSHIBA MK5056GS (scsi)
Disco /dev/sda: 500GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: msdos
Disk Flags: 

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  494GB  494GB   primary   ext4                 arranque
 2      494GB   500GB  6420MB  extended
 5      494GB   500GB  6420MB  logical   linux-swap(v1)


Model: General UDisk (scsi)
Disk /dev/sdc: 1950MB
Tamaño de sector (lógico/físico): 512B/512B
Partition table: msdos
Disk Flags: 

Number  Start       End     Size        Type     File system        Flags
 1      32.3kB  1950MB  1950MB  primary  fat32                arranque
 2      1950MB  1950MB  32.3kB  primary
```

And sudo fdisk -l gives:

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 7.5 GiB, 8053063680 bytes, 15728640 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Disposit.  Inicio Start    Final Sectores  Size Id Tipo
/dev/sda1  *       2048 15728639 15726592  7.5G  c W95 FAT32 (LBA)


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa6a1d2db

Disposit.  Inicio     Start     Final  Sectores   Size Id Tipo
/dev/sdb1  *           2048 964229119 964227072 459.8G 83 Linux
/dev/sdb2         964231166 976771071  12539906     6G  5 Extendida
/dev/sdb5         964231168 976771071  12539904     6G 82 Linux swap / Solaris


```



I tried to recover grub but it didn't work. Please help as I don't know what else to do. Thanks!

P.S.: the system also freezes sometimes, only the current screen gets grey for a while (2 to 10 seconds) then returns normal. Is that right? Computer is at least an i5 with 6 GB RAM and 500 GB HDD.

---

### Post by kansasnoob on 2016-06-11
> I tried to recover grub but it didn't work

I'm curious what method you used? Did you try [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")?

I notice that parted sees the main drive as /dev/sda:

```
Modelo: ATA TOSHIBA MK5056GS (scsi)
Disco** /dev/sda**: 500GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones: msdos
Disk Flags: 

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  494GB  494GB   primary   ext4                 arranque
 2      494GB   500GB  6420MB  extended
 5      494GB   500GB  6420MB  logical   linux-swap(v1)
```

But fdisk sees it as /dev/sdb:

```
Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa6a1d2db

Disposit.  Inicio     Start     Final  Sectores   Size Id Tipo
/dev/sdb1  *           2048 964229119 964227072 459.8G 83 Linux
/dev/sdb2         964231166 976771071  12539906     6G  5 Extendida
/dev/sdb5         964231168 976771071  12539904     6G 82 Linux swap / Solaris
```

I'm not sure why parted sees no /dev/sdb but does see a /dev/sdc ...................... and fdisk shows no /dev/sdc ??????????????????????

Things just look peculiar regarding external drives, but Boot Repair may be able to sort that out.

---

### Post by francisco38 on 2016-06-12
Hi!

Thanks for your fast reply.

I tried first with the HD test that comes with the live CD via USB, but that did't help. Now i tried with Boot-repair you mentioned. Link of results is here:
[http://paste2.org/BO2XnX6B](http://paste2.org/BO2XnX6B)

I have selected sdb (the main HD) as the grub place, not sdb1 (the main partition?).

I had tested and it booted the first time fine.... However next boot was with the same owful message "Operating system not found" :-(

The funny thing is with USB live Ubuntu distro it boots, but not without it... I'll keep testing with the Boot repair, let's see. 
Second attempt with Repair-boot. This is the link:
[http://paste2.org/gchEtPvH](http://paste2.org/gchEtPvH)

Any idea is welcome. Thanks!

Kind regards!

---

### Post by yancek on 2016-06-12
Have you changed the boot priority to boot the hard drive first as suggested at the bottom of the boot repair?  You have Grub code in the MBR pointing to the correct partition with the necessary files.  The grub.cfg file shows your Ubuntu as sdb (set root='hd1,msdos1') so that may need to be changed.

---

