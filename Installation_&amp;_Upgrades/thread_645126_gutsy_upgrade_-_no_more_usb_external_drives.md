---
title: "gutsy upgrade - no more usb external drives"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by dannemil on 2007-12-19
I notice that there a bunch of posts like this, many with no replies. After upgrading to Gutsy, my external seagate hard drive will no longer mount, auto- or manually. I know it is there because when I check it with gparted, it shows up as it should as an ext3 formatted drive (as it did with feisty which mounted it with no problem). Here are the diagnostics:

$dmesg
[ 1510.108000] usb 5-8: new high speed USB device using ehci_hcd and address 5
[ 1510.240000] usb 5-8: configuration #1 chosen from 1 choice
[ 1510.240000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 1510.240000] usb-storage: device found at 5
[ 1510.240000] usb-storage: waiting for device to settle before scanning
[ 1512.684000] device-mapper: table: 254:0: linear: dm-linear: Device lookup failed
[ 1512.684000] device-mapper: ioctl: error adding target to table

That last error repeats indefinitely.

$lsusb
Bus 005 Device 005: ID 0bc2:0501 Seagate RSS LLC 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000  


$ sudo mount -t ext3 /dev/sdb5 /media/usb1
[sudo] password for dannemil:
mount: /dev/sdb5 already mounted or /media/usb1 busy

no matter where I try to mount it it says that it is already mounted, but when I look at it with gparted, it says that /dev/sdb5 is not mounted.

I use that external drive for backups, so I would really like to be able to mount it.

One other piece of evidence: when I plug in a usb flash drive, it automounts just fine and I can read and write to it.

Any help or any other diagnostics that might help me solve this?

---

### Post by taurus on 2007-12-19
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by dannemil on 2007-12-20
> **taurus said:**
> What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

Here are the results of those commands

sudo fdisk -l
[sudo] password for dannemil:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11783    94646916   83  Linux
/dev/sda2           11784       12161     3036285    5  Extended
/dev/sda5           11784       12161     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x546f5c33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32       12161    97434225    5  Extended
/dev/sdb5              32       12161    97434193+  8e  Linux LVM

sdb is the external usb drive

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              89G   69G   16G  82% /
varrun                506M  132K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   35M  472M   7% /lib/modules/2.6.22-14-386/volatile

So sdb does not show up here. Any thoughts?

---

