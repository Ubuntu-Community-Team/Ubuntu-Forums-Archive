---
title: "I made Huge mistake with Gparted"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by gomadorebro1 on 2024-10-29
Hi, I wanted to partition my SSD to do a dual boot with Windows, the problem is that I moved left and right partitions with EFI boot and also Linux Swap and ext4. When I reboot the pc without USB Live stick, the BIOS doesn't find any OS and says "No bootable Device".

[https://imgur.com/a/fD83UIx](https://imgur.com/a/fD83UIx)

```
mint@mint:~$ fdisk -l
fdisk: cannot open /dev/nvme0n1: Permission denied
fdisk: cannot open /dev/sda: Permission denied
fdisk: cannot open /dev/loop0: Permission denied
mint@mint:~$ sudo parted -l
Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? Ignore                                                     
Model: Lexar USB Flash Drive (scsi)
Disk /dev/sda: 247GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      2464kB  9214kB  6750kB               EFI


Model: Micron_2210_MTFDHBA512QFD (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name        Flags
 2      7758MB  8388MB  629MB   fat32                       boot, esp
 3      9017MB  229GB   220GB   ext4            
 4      504GB   512GB   8387MB  linux-swap(v1)              swap


mint@mint:~$ 



```

---

### Post by ubfan1 on 2024-10-29
Can you reset the partitions to what they were?  Best if you get the exact sector numbers for start/end before making any changes, but if you originally used obvious sizes (+220G etc.), maybe the size would work.

---

### Post by gomadorebro1 on 2024-10-29
How to do it?

---

### Post by ubfan1 on 2024-10-29
sudo gdisk -l /dev/nvme0n1  will default output listing to sectors.

---

### Post by gomadorebro1 on 2024-10-29
[HTML]
sudo gdisk -l /dev/nvme0n1
GPT fdisk (gdisk) version 1.0.9

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/nvme0n1: 1000215216 sectors, 476.9 GiB
Model: Micron_2210_MTFDHBA512QFD               
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 0BC64394-A752-40D2-BB5F-2EB3193B21CE
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1000215182
Partitions will be aligned on 2048-sector boundaries
Total free space is 552526445 sectors (263.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2        15153152        16381951   600.0 MiB   EF00  
   3        17610752       447690751   205.1 GiB   8300  
   4       983834624      1000214527   7.8 GiB     8200  
mint@mint:~$ 



[/HTML]

---

### Post by yancek on 2024-10-29
Is the image of gparted output in your first post the 'after' change?  It would be useful it we could see the before.  If you moved the EFI and / filesystem partitions containing boot/grub files, you will likely need to reinstall grub as when the system board looks for the EFI partition, it isn't where it is expected to be.

---

