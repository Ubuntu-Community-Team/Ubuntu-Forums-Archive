---
title: "SWAP not initialized?"
date: 2014-06-02
forum: Installation &amp; Upgrades
---

### Post by kogz on 2014-06-02
Hi,

I use 14.04. I have 16 GB of RAM and two disks (SDD and traditional HDD), on SDD: / and on HDD: /home and swap. After the installation I can see that swap is completely not initialized. SWAP partition seems to be ready.

```
~$ free
             total       used       free     shared    buffers     cached
Mem:      16314468    1899628   14414840     172664      55188     745220
-/+ buffers/cache:    1099220   15215248
Swap:            0          0          0
```

Could you please suggest how can I troubleshoot this?

Thank you!
K

---

### Post by Bashing-om on 2014-06-02
kogz; Humm,

Agreed, not looking like swap is set up. Let's take a look at what the system has set up for swapping:
post back - between code tags - the outputs of terminal commands:
```

sudo blkid
sudo fdisk -lu ## if GPT partitioning requires gdisk instead##
sudo parted -l
cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we will see what is and what might be done.

[INDENT][INDENT][INDENT]where there are solutions 
[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kogz on 2014-06-07
Hi! Thank you Bashin-om for your reply. These are command results:

```
$ sudo blkid
/dev/sda2: UUID="0242e993-eef0-48dc-a93c-039b44ff47de" TYPE="swap" 
/dev/sda3: UUID="c30233c1-55a1-4f6d-aa87-293300a55689" TYPE="ext4" 
/dev/sda4: LABEL="Store" UUID="14B677F7B677D7A6" TYPE="ntfs" 
/dev/sdb1: LABEL="SYSTEM" UUID="3093-7287" TYPE="vfat" 
/dev/sdb2: LABEL="Recovery" UUID="0664941C64941093" TYPE="ntfs" 
/dev/sdb4: LABEL="OS" UUID="50C05001C04FEC32" TYPE="ntfs" 
/dev/sdb5: LABEL="Restore" UUID="DAAE9E1FAE9DF46B" TYPE="ntfs" 
/dev/sdb6: UUID="f53e1887-6b7a-4cae-8606-7b775d06a418" TYPE="ext4" 
```

```
$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9CCBCC4F-225E-4EC0-BC57-C11362EA5179
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 8-sector boundaries
Total free space is 5485 sectors (2.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192        34263039   16.2 GiB    8200  
   3        34263040       993894399   457.6 GiB   8300  
   4       993894400      1953521663   457.6 GiB   0700  Basic data partition

```

```
$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 246162672 sectors, 117.4 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): F4D8EDD4-0472-43F1-9027-C0A5E23B9B41
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 246162638
Partitions will be aligned on 2048-sector boundaries
Total free space is 3245 sectors (1.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848         2050047   900.0 MiB   2700  Basic data partition
   3         2050048         2312191   128.0 MiB   0C01  Microsoft reserved part
   4         2312192       103254015   48.1 GiB    0700  Basic data partition
   5       204197888       246161407   20.0 GiB    2700  Basic data partition
   6       103254016       204197887   48.1 GiB    8300  

```

```
$ sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Dysk /dev/sda: 1000GB
Rozmiar sektora (logiczny/fizyczny): 512B/4096B
Tablica partycji: gpt

Numer  Pocz&#261;tek  Koniec  Rozmiar  System plików   Nazwa                         Flaga
 1     17,4kB    134MB   134MB                    Microsoft reserved partition  msftres
 2     135MB     17,5GB  17,4GB   linux-swap(v1)
 3     17,5GB    509GB   491GB    ext4
 4     509GB     1000GB  491GB    ntfs            Basic data partition          msftdata


Model: ATA SanDisk SDSSDP12 (scsi)
Dysk /dev/sdb: 126GB
Rozmiar sektora (logiczny/fizyczny): 512B/512B
Tablica partycji: gpt

Numer  Pocz&#261;tek  Koniec  Rozmiar  System plików  Nazwa                         Flaga
 1     1049kB    106MB   105MB    fat32          EFI system partition          &#322;adowalna
 2     106MB     1050MB  944MB    ntfs           Basic data partition          ukryta, diag
 3     1050MB    1184MB  134MB                   Microsoft reserved partition  msftres
 4     1184MB    52,9GB  51,7GB   ntfs           Basic data partition          msftdata
 6     52,9GB    105GB   51,7GB   ext4
 5     105GB     126GB   21,5GB   ntfs           Basic data partition          ukryta, diag

```

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=f53e1887-6b7a-4cae-8606-7b775d06a418 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=3093-7287  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda3 during installation
UUID=c30233c1-55a1-4f6d-aa87-293300a55689 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
#UUID=a6567e61-2852-4b15-bd0f-884b75773a8b none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

Thank you for any suggestions!

---

### Post by LastDino on 2014-06-07
Is your swap encrypted? Or did you encrypt home during installation? (There is bug which encrypts swap too if you do so)

Also, the UUID in fstab is not matching the one in output of ''sudo blkid'', replacing that should work, but I've never worked with encrypted swaps, so I would wait for someone else to address the issue just in case.

---

### Post by kogz on 2014-06-08
Yes, my home was encrypted during installation. It might be this bug, is there any description of it and how to proceed?

Please also let me tell you that during my troubleshooting I formatted swap partition using gpated, so now swap aprtition is most probably not encrypted and this can explain why UUID is different. How should I modify my fstab to use unencrypted swap partition or make my swap partition encrypted again?

Thank you!

---

### Post by obake2 on 2014-06-10
This seems to be a bug with Ubuntu 14.04:

[http://ubuntuforums.org/showthread.php?t=2221067](http://ubuntuforums.org/showthread.php?t=2221067)



Please add yourself to the Launchpad Bug reports that are listed on that link. :smile:
I'm also affected by this bug and waiting for a proper fix.

---

