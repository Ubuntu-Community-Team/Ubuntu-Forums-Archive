---
title: "Install 14.04 Desktop with second EFI partition"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by geohei on 2014-08-03
Hi.

```
geohei@deimos:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sdb: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7B2A6511-D248-41E6-BB41-8F15451740AA
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 38072941 sectors (18.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  Windows 7 (ESP)
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       210184191   100.0 GiB   0700  Basic data partition
   4       210184192       315041791   50.0 GiB    0700  Basic data partition
   5       315041792       315246591   100.0 MiB   EF00  Ubuntu 14.04 (ESP)
   6       315246592       420104191   50.0 GiB    8300  Ubuntu 14.04
   7       420104192       462047231   20.0 GiB    8200  Linux swap
```
I have a dual boot system installed on my SSD (GPT).
1. Windows 7
2. Ubuntu 14.04

I'd like to use a separate EFI partition for Ubuntu (for separate backup/restore operations and potential mutual interfeneces duer Windows 7 / Ubuntu EFI updates).

How can I instruct Ubuntu 14.04 during installation procedure to use sdb5 as EFI instead of sdb1?

Thanks!

---

### Post by oldfred on 2014-08-03
You cannot currently.

I understand UEFI spec does technically allow multiple efi partitions, but currently no system works with more than one efi partition per device.

But each install has a separate folder in the efi partition, so they are separate.

Typical structure in efi partition:

 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

---

### Post by ubfan1 on 2014-08-03
Since the Ubuntu bootloaders are kept in a separate directory (/EFI/ubuntu), there is little chance of interference with the Windows bootloaders in /EFI/Microsoft/Boot/.  Only one efi partition is allowed per device, but I don't know if just removing the boot flag would be enough to make the second one "invisible".  Anyway, having to change the partition table to change OSes is a very dangerous thing, if you mess up the partition table, you really will be in recovery pain.  Just use the supplied EFI partition (100M is smaller than I prefer, but really, even with Ubuntu bootloaders added, and a vendor backup in place, only about 55M will be used.

---

### Post by geohei on 2014-08-15
What do you think of this here: [Move Ubuntu 14.04 Desktop ESP partition]("http://www.geohei.lu/geoheiWP/?p=85")

It took me a while ... but it works!

---

### Post by oldfred on 2014-08-15
Glad you found a solution.

That is the first time I have seen anyone try to make two efi partitions work.

But I am not sure it really is needed anyway. He has multiple drives and a better configuration would be Windows on one drive and Ubuntu on another drive. then each hard drive would have its own efi partition without issue.

And the issue of backup can be controlled just by separately backing up the efi partition and making sure that backup occurs any time any other operating system install is updated or backed up.

---

### Post by geohei on 2014-08-15
He = me (I wrote the article) :p

I'm also not sure it's really needed. Time will see ... and for the updates ... a simultaneous update would indeed be a possible solution (let me think about that).

---

