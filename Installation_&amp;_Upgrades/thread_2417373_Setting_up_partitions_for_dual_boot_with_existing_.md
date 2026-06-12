---
title: "Setting up partitions for dual boot with existing Arch install"
date: 2019-04-22
forum: Installation &amp; Upgrades
---

### Post by jiv222 on 2019-04-22
Hello,

I am currently running an arch install configured with Luks on LVM.  I would like to dual boot with a shared /home partition, with two separate users.  I have gotten as far as booting into the Ubuntu live installer and unlocking the luks encryption, but the installer does not recognize the Arch Operating system.  I am currently using systemd-boot on Arch.  I am not sure how to configure the lvm partitions in this manner, so any help or direction would be great. 

Here is my fdisk -l:
```
Disk /dev/loop0: 1.8 GiB, 1905045504 bytes, 3720792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: DD0AFA23-B5D9-4394-B53D-5E136CD8DF0C

Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048   1050623   1048576  512M EFI System
/dev/nvme0n1p2 1050624 500118158 499067535  238G Linux filesystem


Disk /dev/sda: 57.3 GiB, 61505273856 bytes, 120127488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x40993ab6

Device     Boot   Start     End Sectors  Size Id Type
/dev/sda1  *          0 3899391 3899392  1.9G  0 Empty
/dev/sda2       3830956 3835883    4928  2.4M ef EFI (FAT-12/16/32)


Disk /dev/mapper/lvm: 238 GiB, 255520480768 bytes, 499063439 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/MyVol-swap: 8 GiB, 8589934592 bytes, 16777216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/MyVol-root: 25 GiB, 26843545600 bytes, 52428800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/MyVol-home: 205 GiB, 220083519488 bytes, 429850624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

Thanks

---

### Post by &amp;wP*!) on 2019-08-07
Haven't used LVM but using a shared /home among many OS might be problematic because a certain application can have different versions on both OSes which could behave differently in both distros for a certain settings. I recommend not to share /home/$USER directories. Use a separate partition or volume instead.

---

