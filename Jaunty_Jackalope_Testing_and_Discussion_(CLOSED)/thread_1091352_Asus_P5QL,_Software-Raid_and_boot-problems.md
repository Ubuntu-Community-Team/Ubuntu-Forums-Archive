---
title: "Asus P5QL, Software-Raid and boot-problems"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tnat on 2009-03-09
Hello,

i'm working for weeks now on an really annoying problem. I have a Asus P5QL board with the Intel G43 chipset. There are 4 sata 2,5" harddisk (WDC WD1600BEKT-00F3T0) and 2 sata DVD/RW drives connected.

I use md-raid0 for my root-filesystem.

Since the kernel 2.6.28-6 (with the corresponding initrd, hal and udev) i am unable to boot. ...gave up while waiting for root-device...

When i update the initrd for the kernel 2.6.28-5, this kernel is also unable to boot.
If i use the last alpha 5 for installing, same problem.

When i'm stuck in the busybox, the /proc/partitions only shows the drives themselve, and no partition. /dev/sda, dev/sdb, ... no /dev/sda1, /dev/sda2, ...

The curiosity is, that sometimes one or more of the partitions shows up in the /proc/partitions. 9/10 times of trying to boot, only the drives are there.

So i am unable to start the raid because of missing partitions.

Infos of my last running system booted with 2.6.28-4.

```
thomas@edv03:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid0 sdd4[0] sdc4[1] sda4[2] sdb4[3]
      543092992 blocks 64k chunks
      
md0 : active raid0 sdd2[0] sdc2[1] sda2[2] sdb2[3]
      39069696 blocks 64k chunks
      
md1 : active raid0 sdd3[0] sdc3[1] sda3[2] sdb3[3]
      39069696 blocks 64k chunks
      
unused devices: <none>

```

```
thomas@edv03:~$ sudo fdisk -l /dev/sda

Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000dc325

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1         122      979933+  82  Linux Swap / Solaris
/dev/sda2           18242       19457     9767520   fd  Linux raid autodetect
/dev/sda3           17026       18241     9767520   fd  Linux raid autodetect
/dev/sda4             123       17025   135773347+  fd  Linux raid autodetect

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

```
thomas@edv03:~$ sudo fdisk -l /dev/sdb

Platte /dev/sdb: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000e21e5

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1         122      979933+  82  Linux Swap / Solaris
/dev/sdb2           18242       19457     9767520   fd  Linux raid autodetect
/dev/sdb3           17026       18241     9767520   fd  Linux raid autodetect
/dev/sdb4             123       17025   135773347+  fd  Linux raid autodetect

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

```
thomas@edv03:~$ sudo fdisk -l /dev/sdc

Platte /dev/sdc: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00028fa8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1               1         122      979933+  82  Linux Swap / Solaris
/dev/sdc2           18242       19457     9767520   fd  Linux raid autodetect
/dev/sdc3           17026       18241     9767520   fd  Linux raid autodetect
/dev/sdc4             123       17025   135773347+  fd  Linux raid autodetect

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

```
thomas@edv03:~$ sudo fdisk -l /dev/sdd

Platte /dev/sdd: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000cdbb8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdd1   *           1         122      979933+  83  Linux
/dev/sdd2           18242       19457     9767520   fd  Linux raid autodetect
/dev/sdd3           17026       18241     9767520   fd  Linux raid autodetect
/dev/sdd4             123       17025   135773347+  fd  Linux raid autodetect

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

not working:
```
title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic
uuid		d68d0d6a-3515-4921-8b15-a138494bbbd1
kernel		/vmlinuz-2.6.28-8-generic root=/dev/md0 ro quiet splash 
initrd		/initrd.img-2.6.28-8-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-8-generic (recovery mode)
uuid		d68d0d6a-3515-4921-8b15-a138494bbbd1
kernel		/vmlinuz-2.6.28-8-generic root=/dev/md0 ro  single
initrd		/initrd.img-2.6.28-8-generic

```

working:
```
title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic
uuid		d68d0d6a-3515-4921-8b15-a138494bbbd1
kernel		/vmlinuz-2.6.28-4-generic root=/dev/md0 ro quiet splash 
initrd		/initrd.img-2.6.28-4-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-4-generic (recovery mode)
uuid		d68d0d6a-3515-4921-8b15-a138494bbbd1
kernel		/vmlinuz-2.6.28-4-generic root=/dev/md0 ro  single
initrd		/initrd.img-2.6.28-4-generic

```

the working /proc/partitions
```
thomas@edv03:~$ cat /proc/partitions 
major minor  #blocks  name

   8        0  156290904 sda
   8        1     979933 sda1
   8        2    9767520 sda2
   8        3    9767520 sda3
   8        4  135773347 sda4
   8       16  156290904 sdb
   8       17     979933 sdb1
   8       18    9767520 sdb2
   8       19    9767520 sdb3
   8       20  135773347 sdb4
   8       32  156290904 sdc
   8       34    9767520 sdc2
   8       35    9767520 sdc3
   8       36  135773347 sdc4
   8       48  156290904 sdd
   8       49     979933 sdd1
   8       50    9767520 sdd2
   8       51    9767520 sdd3
   8       52  135773347 sdd4
   9        1   39069696 md1
   9        0   39069696 md0
   9        2  543092992 md2

```

```
thomas@edv03:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

Whats the Problem since 2.6.28-6, or is a update of udev or hal the evil?

Thanks for help,
Thomas

---

