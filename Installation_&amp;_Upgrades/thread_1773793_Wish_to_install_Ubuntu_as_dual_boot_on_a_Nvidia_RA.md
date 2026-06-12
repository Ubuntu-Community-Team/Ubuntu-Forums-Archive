---
title: "Wish to install Ubuntu as dual boot on a Nvidia RAID"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by jaezcurra on 2011-06-02
Hi, I am currently with Wubi 10.04 under Vista and my Dell XPS 630i has a 1 TB Nvidia RAID controller.
Here are my BootInfo output, as well as my fdisk -l output:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/mapper/nvidia_bcidhdja.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: tipo de sistema de ficheros '' desconocido

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: tipo de sistema de ficheros '' desconocido
mount: tipo de sistema de ficheros '' desconocido

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: tipo de sistema de ficheros '' desconocido
mount: tipo de sistema de ficheros '' desconocido
mount: tipo de sistema de ficheros '' desconocido

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvidia_bcidhdja1: ______________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

nvidia_bcidhdja2: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

nvidia_bcidhdja3: ______________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot/grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

nvidia_bcidhdja3/Wubi: _________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,116,928 1,469,724,671 1,448,607,744   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disco /dev/sdc: 750.2 GB, 750156374016 bytes
255 cabezas, 63 sectores/pista, 91201 cilindros, 1465149168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 1,465,144,064 1,465,144,002   7 NTFS / exFAT / HPFS


Drive: nvidia_bcidhdja _____________________________________________________________________

Disco /dev/mapper/nvidia_bcidhdja: 1000.2 GB, 1000204884992 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros, 1953525166 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/nvidia_bcidhdja1                 63       144,584       144,522  de Dell Utility
/dev/mapper/nvidia_bcidhdja2            145,408    21,116,927    20,971,520   7 NTFS / exFAT / HPFS
/dev/mapper/nvidia_bcidhdja3   *     21,116,928 1,469,724,671 1,448,607,744   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       05c07072-8647-4893-9f2a-0e0eb1df1f15   ext4       
/dev/mapper/nvidia_bcidhdja1 07D8-0807                              vfat       DellUtility
/dev/mapper/nvidia_bcidhdja2 D06A89A06A898446                       ntfs       RECOVERY
/dev/mapper/nvidia_bcidhdja3 E03E8C863E8C5804                       ntfs       OS
/dev/sda                                                nvidia_raid_member 
/dev/sdb                                                nvidia_raid_member 
/dev/sdc1        8A34D58734D57723                       ntfs       IOMEGA_HDD

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
nvidia_bcidhdja
nvidia_bcidhdja1
nvidia_bcidhdja2
nvidia_bcidhdja3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/mapper/nvidia_bcidhdja3 /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdc1        /media/IOMEGA_HDD_       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


===================== nvidia_bcidhdja3/boot/grub/grub.cfg: =====================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/mapper/nvidia_bcidhdja3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
	linux /boot/vmlinuz-2.6.31-17-generic root=/dev/mapper/nvidia_bcidhdja3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-17-generic
}

### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/mapper/nvidia_bcidhdja3)" {
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

============= nvidia_bcidhdja3: Location of files loaded by Grub: ==============

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.31-16-generic             32549
            ?? = ??             boot/initrd.img-2.6.31-17-generic             32549
            ?? = ??             boot/vmlinuz-2.6.31-16-generic                32549
            ?? = ??             boot/vmlinuz-2.6.31-17-generic                32549

================== nvidia_bcidhdja3/Wubi/boot/grub/grub.cfg: ===================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-32-generic" {
	insmod ntfs
	set root='(hd3,3)'
	search --no-floppy --fs-uuid --set e03e8c863e8c5804
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-32-generic root=/dev/mapper/nvidia_bcidhdja3 loop=/ubuntu/disks/root.disk ro   quiet splash noapic nolapic
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, Linux 2.6.32-32-generic (recovery mode)" {
	insmod ntfs
	set root='(hd3,3)'
	search --no-floppy --fs-uuid --set e03e8c863e8c5804
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-32-generic root=/dev/mapper/nvidia_bcidhdja3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, Linux 2.6.32-31-generic" {
	insmod ntfs
	set root='(hd3,3)'
	search --no-floppy --fs-uuid --set e03e8c863e8c5804
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-31-generic root=/dev/mapper/nvidia_bcidhdja3 loop=/ubuntu/disks/root.disk ro   quiet splash noapic nolapic
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, Linux 2.6.32-31-generic (recovery mode)" {
	insmod ntfs
	set root='(hd3,3)'
	search --no-floppy --fs-uuid --set e03e8c863e8c5804
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-31-generic root=/dev/mapper/nvidia_bcidhdja3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-31-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

======================= nvidia_bcidhdja3/Wubi/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

=========== nvidia_bcidhdja3/Wubi: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

   0.419578552 = 0.450519040    boot/grub/grub.cfg                             1
  12.746135712 = 13.686059008   boot/initrd.img-2.6.32-31-generic              2
  13.904315948 = 14.929645568   boot/initrd.img-2.6.32-32-generic              3
   5.892761230 = 6.327304192    boot/vmlinuz-2.6.32-31-generic                 2
   1.954708099 = 2.098851840    boot/vmlinuz-2.6.32-32-generic                 2
  13.904315948 = 14.929645568   initrd.img                                     3
  12.746135712 = 13.686059008   initrd.img.old                                 2
   1.954708099 = 2.098851840    vmlinuz                                        2
   5.892761230 = 6.327304192    vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3



========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No existe el fichero o el directorio
hexdump: /dev/sda1: No existe el fichero o el directorio
hexdump: /dev/sda2: No existe el fichero o el directorio
hexdump: /dev/sda2: No existe el fichero o el directorio
hexdump: /dev/sda3: No existe el fichero o el directorio
hexdump: /dev/sda3: No existe el fichero o el directorio

```
```


Disco /dev/mapper/nvidia_bcidhdja: 1000.2 GB, 1000204884992 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xd8000000

                   Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/mapper/nvidia_bcidhdja1               1           9       72261   de  Utilidad Dell
/dev/mapper/nvidia_bcidhdja2              10        1315    10485760    7  HPFS/NTFS
/dev/mapper/nvidia_bcidhdja3   *        1315       91487   724303872    7  HPFS/NTFS

Disco /dev/mapper/nvidia_bcidhdja1: 73 MB, 73995264 bytes
255 cabezas, 63 sectores/pista, 8 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x8a42b4c3

Esto no parece una tabla de particiones
Probablemente ha seleccionado el dispositivo que no era.

                     Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/mapper/nvidia_bcidhdja1p1            1880      111816   883058677+  cd  Desconocido
La partición 1 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(0, 190, 62) lógicos=(1879, 146, 63)
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(257, 19, 50) lógicos=(111815, 75, 50)
La partición 1 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja1p2   ?       33873      138704   842053558   72  Desconocido
La partición 2 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(101, 107, 32) lógicos=(33872, 185, 42)
La partición 2 tiene distintos finales físicos/lógicos:
     físicos=(370, 114, 47) lógicos=(138703, 139, 40)
La partición 2 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja1p3   ?       69058       69060       10020+  45  Desconocido
La partición 3 tiene distintos principios físicos/lógicos (¿no Linux?):
     físicos=(68, 114, 0) lógicos=(69057, 206, 23)
La partición 3 tiene distintos finales físicos/lógicos:
     físicos=(322, 76, 12) lógicos=(69059, 14, 29)
La partición 3 no termina en un límite de cilindro.

Disco /dev/mapper/nvidia_bcidhdja2: 10.7 GB, 10737418240 bytes
255 cabezas, 63 sectores/pista, 1305 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x2052474d

Esto no parece una tabla de particiones
Probablemente ha seleccionado el dispositivo que no era.

                     Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/mapper/nvidia_bcidhdja2p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
La partición 1 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja2p2   ?      121585      234786   909287957+  43  Desconocido
La partición 2 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja2p3   ?       14052       14052           5   72  Desconocido
La partición 3 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja2p4          164483      164486       25945    0  Vacía
La partición 4 no termina en un límite de cilindro.

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/mapper/nvidia_bcidhdja3: 741.7 GB, 741687164928 bytes
255 cabezas, 63 sectores/pista, 90171 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x2052474d

Esto no parece una tabla de particiones
Probablemente ha seleccionado el dispositivo que no era.

                     Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/mapper/nvidia_bcidhdja3p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
La partición 1 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja3p2   ?      121585      234786   909287957+  43  Desconocido
La partición 2 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja3p3   ?       14052       14052           5   72  Desconocido
La partición 3 no termina en un límite de cilindro.
/dev/mapper/nvidia_bcidhdja3p4          164483      164486       25945    0  Vacía
La partición 4 no termina en un límite de cilindro.

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xd8000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1           9       72261   de  Utilidad Dell
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       91487   724303872    7  HPFS/NTFS

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0xd8000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1           9       72261   de  Utilidad Dell
/dev/sdb2              10        1315    10485760    7  HPFS/NTFS
/dev/sdb3   *        1315       91487   724303872    7  HPFS/NTFS

```

It seems that Ubuntu is seeing the RAID, so I should be able to install 11.04 on it.

In fact, I have booted live and simulated the space allocation.  
Here are two images of it:

[IMG][http://i1104.photobucket.com/albums/h327/jaezcurra/th_Pantallazo1.png](http://s1104.photobucket.com/albums/h327/jaezcurra/?action=view&current=Pantallazo1.png)[/IMG]
[IMG][http://i1104.photobucket.com/albums/h327/jaezcurra/th_Pantallazo2.png](http://s1104.photobucket.com/albums/h327/jaezcurra/?action=view&current=Pantallazo2.png)[/IMG]

First image (Option A) suggests /dev/sda as device for boot loader installation, while second image (Option B) suggests /dev/mapper/nvidia_bcidhdja.

I think that the way of keeping the RAID would be using Option B as the device for boot loader installation.  Would Option A break the RAID instead?

Any suggestion?

---

### Post by jaezcurra on 2011-06-03
Bump

---

