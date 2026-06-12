---
title: "Maverick Installer doesn't recognize existing partition list"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by berkanic on 2010-10-13
I have been upgrading from 9.04 to 10.04. Now, I want to install 10.10 from the beginning without losing the data in my current partitions but when I run the Maverick installer it recognize my disk as a whole with no partitions. From another posts, I suspect that the problem is in the partition list because it seems to be a duplicate partition but don't know how to fix it. This is the fdisk output:

```
jgarcia@jgarcia-laptop:~$ sudo fdisk -lu /dev/sda

Disco /dev/sda: 250.1 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros, 488397168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00000080

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *   484183098   488392064     2104483+   c  W95 FAT32 (LBA)
/dev/sda2           96390   125933534    62918572+   7  HPFS/NTFS
/dev/sda3       165003615   488392064   161694225    f  W95 Ext'd (LBA)
/dev/sda4       125933535   165003614    19535040   83  Linux
/dev/sda5       484183098   488392064     2104483+  dd  Desconocido
/dev/sda6       480279303   484183034     1951866   82  Linux swap / Solaris
/dev/sda7       343550088   480263174    68356543+   b  W95 FAT32
/dev/sda8       165003741   343533959    89265109+  83  Linux

Las entradas de la tabla de particiones no están en el orden del disco

```

As it can be seen, /dev/sda5 is a duplicate of /dev/sda1. By the way, "Desconocido" means "Unknown". 

Also, Parted reports the problem:

```
 sudo parted /dev/sda print
Error: No se puede tener particiones superpuestas. 
```

Which means It can't be overlapped partitions.

How can I fix this issue safely? I really want to install 10.10!

---

### Post by oldfred on 2010-10-13
I would try testdisk. Is sda2 a win7 install and is/was sda1 the standard 100MB boot/repair hidden partition for windows to boot? It shows boot flag on sda1 and you have space in front of sda2.

You still need good backups before any partition changes.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by dhysk on 2010-10-13
If oldfred's doesn't work than you could try what I did.

first I would backup the partion list by 
```
sudo sfdisk -d /dev/sdc > parts.txt
```
and put that file on a thumb drive or something removable.

that way you can try to delete the sda5 partition and see what happens.  If you cannot mount and see the data on the other partitions than the data would be lost if you kept it that way.  If this happens than just redo instate your old partition table by
```
sudo sfdisk /dev/sdc < parts.txt
```

you may need to add the --force option to get it to write it back.  This should.. i mean should.. give you all you're data back.  However know that nothing can be guaranteed.  It worked for me but I knew I could use file carvers and data recovery tools to get it back if I had too, luckily I didn't.

For me it was a swap partition that overlapped an extended partition that caused the problem.  I found it by removing one partition at a time untill the installer could see the table.  I than rewrote the original table and removed the one problem candidate(in this case the swap partition).

---

