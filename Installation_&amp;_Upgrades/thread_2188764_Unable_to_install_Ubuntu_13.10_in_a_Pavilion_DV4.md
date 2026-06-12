---
title: "Unable to install Ubuntu 13.10 in a Pavilion DV4"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by emarrodz7 on 2013-11-18
Hi everyone.

I'm trying to install 13.10 on my HP Pavilion DV4 alongside the OEM OS, Windows 7. I already tried an external and internal CD/DVD reader and no luck, after a short I select it to install it asks for a reboot, ejects the DVD and simply goes to Windows.

It is important to keep the Windows installation so what am I missing? I read I had to install from an USB HDD but I've no idea on how to do that.

Thanks in advance for any clue!

---

### Post by fantab on 2013-11-19
I think you must set it in BIOS to boot CD/DVD first. You check in 'Boot Order' or Boot Priority or something on those lines. Default will be HDD, temporarily you will have change it to boot from DVD.

---

### Post by emarrodz7 on 2013-11-19
Thanks for your answer. The steps you describe were applied, as always when I install a new OS. The problem is AFTER I boot the installation interface. When I finish selecting my preference of Ubuntu to be installed alongside Win7, the computer ejects the DVD and ask for a reboot, but then Win7 starts normally (as expected since nothing was installed and the DVD was removed).

I already reviewed all BIOS configs but I see no clue on what else to configure (which is not much as the interface for BIOS is very basic).

So, any other idea?

Thanls in advance!

---

### Post by fantab on 2013-11-19
Instead of trying to 'Install' use the option 'try Ubuntu without installing' and tell us what happens.

If you reach the desktop using the above option then , open the Terminal [ctrl+alt+T] and post the output of the following commands:
```
sudo parted -l
sudo fdisk -l
```

Sounds like you've hit the ONLY 4 Primary Partition Limit, which is common with HP machines.

---

### Post by emarrodz7 on 2013-11-22
Thanks for the follow up. These are the results I got. Please be aware they are in Spanish but I believe they are pretty much transparent to be understood, in case something is not clear please let me know to translate:

ubuntu@ubuntu:~$ sudo parted -l
Modelo: ATA Hitachi HTS54756 (scsi)
Disco /dev/sda: 640GB
Tamaño de sector (lógico/físico): 512B/4096B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  210MB  209MB   primary  ntfs                 arranque
 2      210MB   607GB  607GB   primary  ntfs
 3      607GB   636GB  28,6GB  primary  ntfs
 4      636GB   640GB  4260MB  primary  fat32                lba


Error: ¡No se puede hacer una partición fuera del disco!                  

ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros, 1250263728 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0xab30a3b6

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600  1186013183   592801792    7  HPFS/NTFS/exFAT
/dev/sda3      1186013184  1241939967    27963392    7  HPFS/NTFS/exFAT
/dev/sda4      1241939968  1250260991     4160512    c  W95 FAT32 (LBA)

Thanks again for your help!

---

### Post by fantab on 2013-11-22
The 'msdos' partition table limits itself to only four primary partitions. And as you can see HP has used up all four Primary partitions. There is no place for Ubuntu to install.
So, you need to delete one partition, shrink another, if more space is needed. Then create an Extended Partition. 

See this for more details: [http://ubuntuforums.org/showthread.php?t=2186301](http://ubuntuforums.org/showthread.php?t=2186301)

If you have any doubts do ask. And post a Screenshot of your HDD partitions from Windows.

---

### Post by emarrodz7 on 2013-11-22
Thanks a lot. I imagined something like this. I'll review my options. Is it possible to install to an external HDD and boot from it each time I want to use it?

---

### Post by fantab on 2013-11-22
> **emarrodz7 said:**
> ... Is it possible to install to an external HDD and boot from it each time I want to use it?

Yes you can install Ubuntu on a Ext HDD...
To be able to boot from it you will have to enable USB booting in BIOS and also make USB device your first boot device. It should top the boot priority.
GRUB boot-loader MUST be installed on this Ext HDD ONLY.

However it will be better if you install it to the internal HDD as from Int. HDD Ubuntu will run faster.
HP usually has a partition (a small one) dedicated entirely to its Utilities. Generally this parttition will be safe to delete after copying the contents of the partition to an external device.
If you want, you can make a full backup/clone of the HDD in its present shape to an external device, then go on to install Ubuntu after 'managing' your HDD. This way you will be able to restore your machine to its original state, if and when you want.

---

