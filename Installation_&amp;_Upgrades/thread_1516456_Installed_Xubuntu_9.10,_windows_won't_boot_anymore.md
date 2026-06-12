---
title: "Installed Xubuntu 9.10, windows won't boot anymore."
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by curambar on 2010-06-23
let's start:
```
Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xd4b0d4b0

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *         707        3950    26057398+   7  HPFS/NTFS
/dev/sda2            3951        4819     6980242+  83  Linux
/dev/sda3               2         706     5662912+   f  W95 Ext'd (LBA)
/dev/sda4            4820        4865      369495   82  Linux swap / Solaris
/dev/sda5               2         706     5662881    7  HPFS/NTFS

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 2063 MB, 2063597568 bytes
16 cabezas, 32 sectores/pista, 7872 cilindros
Unidades = cilindros de 512 * 512 = 262144 bytes
Identificador de disco: 0x00000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        7872     2015216    b  W95 FAT32
```Yes, I'm from Argentina, so I'm using Xubuntu in spanish.

Thing is, after I installed xubuntu, GRUB gives me the option to boot from Win XP, as expected. But when I select that option, it says something like this (i'm translating it back to english):
```
Windows XP won't load.
disk/system32/something.sys not found. Install the file and try again
```grub.cfg displays this:
```
insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0638cc9438cc8461
    drivemap -s (hd0) ${root}
    chainloader +1
```I tried to change it to (hd0,0) and (hd0,4) but it's still not working.

Ideas?


Also, in another subject... how can I read those NTFS partitions from xubuntu?

Thanks!!

---

### Post by Custom Cowboy on 2010-06-29
You can try in terminal "sudo update-grub" to find all operating systems and update GRUB information

---

