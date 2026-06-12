---
title: "Wd My book essential 1 Tb usb 3.0 problem"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by Thindriver on 2013-01-05
Hi i'm new in this forum.
I would like to link one external hdd ( WD My book essential usb 3.0).
I have Windows in one partition and in another partition Ubuntu 12.04 .
So when i plug in the hdd and Windows recognizes one hdd.
When i tried to put My book essential in Ubuntu ,show an error message and if i go  in file manager , i can't find anything .
```
Error mounting: mount exited with exit code 12: NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
I tried lsusb and  the result is this :
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. 
Bus 002 Device 003: ID 1058:1130 Western Digital Technologies, Inc. 

```
After this i tried sudo fdisk -l command and the result is this :
```
Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 testine, 63 settori/tracce, 121597 cilindri, totale 1953458176 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x2052474d

Questa non sembra una tabella delle partizioni.
Probabilmente è stato scelto il dispositivo sbagliato.

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
/dev/sdb2   ?  1953251627  3771827541   909287957+  43  Sconosciuto
/dev/sdb3   ?   225735265   225735274           5   72  Sconosciuto
/dev/sdb4      2642411520  2642463409       25945    0  Vuoto

```
How can i fix it?

---

### Post by ajgreeny on 2013-01-05
I do not understand the language but I can see that none of the partitions noted are shown as NTFS which is what I assume you think they should be.
What is the DiskSecure Multi-Boot partition?
I do not recognise the format Id references either, so what does ```
sudo parted -l
``` show us?
I wonder if the disk is formatted with GPT partitions and if that is causing this problem.

Perhaps you need to backup any files on it and format it again?

---

### Post by Thindriver on 2013-01-05
Sorry i repost   the  result of sudo fdisk -l
```
Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?     6579571  1924427647   958924038+  70  DiskSecure Multi-Boot
/dev/sdb2   ?  1953251627  3771827541   909287957+  43  Unknown
/dev/sdb3   ?   225735265   225735274           5   72  Unknown
/dev/sdb4      2642411520  2642463409       25945    0  Empty

Partition table entries are not in disk order

```
Sudo parted -i result:
```
Model: WD My Book 1130 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ntfs


```
I don't know what is  DiskSecure Multi-Boot partition .
The problem is that in Windows there are only 1 partition and in Ubuntu there are three "hidden" partition.
I prefer don't format beacuse :
1- there a lot of data and i won't make a back up of it :)
2- i think that is a driver problem and not a partition problem (the reason is the number of partition in ubuntu) but i can wrong.

---

