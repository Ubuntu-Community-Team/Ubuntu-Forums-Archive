---
title: "cdrecord doesn´t detect my cdr"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by cirpo on 2005-05-19
hi, i installed ubuntu, everything works fine except my cdr...

First it seems strange that the devices are inverted(hda becomes hde and so on),but  
   there are no problems except with cdrecord
If I run > cdrecord --scanbus dev=ATA 
cdrecord tries to open hdb> scsidev: 'ATA'
devname: 'ATA'
scsibus: -2 target: -2 lun: -2
Warning: Using badly designed ATAPI via /dev/hd* interface.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hdb'. Cannot open SCSI driver. 

but dmesg says:
>  dmesg | grep hdg
Kernel command line: root=/dev/hde3 ro quiet splash vga=792 hdg=ide-cd
ide_setup: hdg=ide-cd
    ide3: BM-DMA at 0x9008-0x900f, BIOS settings: hdg:DMA, hdh:pio
hdg: PHILIPS DVDR1640P, ATAPI CD/DVD-ROM drive
hdg: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache


I have also to say that i have a pci ide controller

thanks in advance

---

### Post by defkewl on 2005-05-19
Could you please paste your /etc/fstab here

---

### Post by cirpo on 2005-05-19
my /etc/fstab:

> nina@nina ~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hde3       /               reiserfs defaults       0       1
/dev/hde1       /boot           ext2    defaults        1       1
/dev/hde5       none            swap    sw              0       0
/dev/hdd1       /home/archive   ext3    noatime         0       0
/dev/hdb1       /home/archive/media   reiserfs    noatime        0       2
/dev/hdc1       /home/archive/media/movies reiserfs noatime     0       3
/dev/hdg        /media/cdrom    iso9660         ro,user,noauto  0  0
nina@nina ~ $

---

### Post by dumbbeatnix on 2005-08-23
So what was the result ?

What did they need to change to their fstab file ?

Please post solutions !!!

 ](*,)  ](*,)  ](*,)

---

