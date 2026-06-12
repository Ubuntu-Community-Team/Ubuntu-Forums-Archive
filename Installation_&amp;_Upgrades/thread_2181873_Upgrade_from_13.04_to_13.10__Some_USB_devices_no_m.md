---
title: "Upgrade from 13.04 to 13.10 : Some USB devices no more work"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by infolix76 on 2013-10-19
Hi,

I upgraded my system from a Ubuntu lowlatency 13.04 to 13.10.
Everything seemed to have worked correctly.
To my astonishement, none of my USB keys or external disks will work any longer although my USB keyboard and mouse do.
Their little LED light don't show as if they were not powered any longer.

lsusb gives :

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 007 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo parted --list gives :

Modèle: ATA WDC WD2500HHTZ-0 (scsi)
Disque /dev/sda : 250GB
Taille des secteurs (logiques/physiques): 512B/4096B
Table de partitions : gpt

Numéro  Début   Fin     Taille  Système de fichiers  Nom  Fanions
 1      1049kB  99,6MB  98,6MB  fat32                     démarrage
 2      99,6MB  242GB   242GB   ext4                      msftdata
 3      242GB   250GB   8002MB  linux-swap(v1)


Modèle: ATA SAMSUNG HD203WI (scsi)
Disque /dev/sdb : 2000GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      32,3kB  2000GB  2000GB  primary  ntfs
 
 ls /dev/sd* gives :
 
 /dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1

Anybody had this issue before ?
Should I go back to 13.04 quickly?

Thanks for any answer.

---

### Post by Frogs Hair on 2013-10-19
> Should I go back to 13.04 quickly?

You would have to do a clean installation of 13.04. You can check Launchpad for bugs , but if you need your system up and running you may not want to wait. My printer and other usb devices are working.

---

### Post by infolix76 on 2013-10-20
Do you mean I REALLY have to go back to 13.04 to have my USB devices working again?
By upgrading I expected to get MORE functionalities not LESS...

---

