---
title: "Installing on SSD"
date: 2015-06-30
forum: Installation &amp; Upgrades
---

### Post by smrcek2 on 2015-06-30
Hello I'm new to Ubuntu, so I'll be installing 14.04 Ubuntu on a single new Samsung 850 evo 120GB SSD which installation type would be best? If custom manually would I need to align partitions?

---

### Post by oldfred on 2015-06-30
Is system UEFI or BIOS?

I do prefer to use gparted to create partitions in advance if you know and understand a bit about partitions and Something Else install. But with a 120GB drive a default install of / (root) & swap is ok. I just prefer smaller / partitions, but that applies more for hard drives to reduce seek time and multi-booting where you want separate data partiiton(s).

I now prefer gpt partitioning. But if dual booting with Windows, you can only boot in UEFI mode with gpt. Ubuntu can use gpt for BIOS if you have a tiny 1 or 2MB unformatted partition with the bios_grub flag or if UEFI you must have the ESP - efi system partition.

Newer versions of gparted or installer automatically install aligned.

---

### Post by smrcek2 on 2015-07-03
Booted from UEFI selected install Ubuntu made custom partitions is it correct?

sudo parted -l
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number Start End Size File system Name Flags
1 1049kB 2097kB 1049kB bios_grub
2 2097kB 553MB 551MB fat32 boot
3 553MB 20,6GB 20,0GB ext4
4 20,6GB 116GB 95,0GB ext4
5 116GB 120GB 4482MB linux-swap(v1)





sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
MBR: protective
BSD: not present
APM: not present
GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number Start (sector) End (sector) Size Code Name
1 2048 4095 1024.0 KiB EF02
2 4096 1079295 525.0 MiB EF00
3 1079296 40140799 18.6 GiB 8300
4 40140800 225687551 88.5 GiB 8300
5 225687552 234440703 4.2 GiB 8200

---

### Post by oldfred on 2015-07-03
You have both the bios_grub & ESP partitions.

Only one or the other is required, but I have always added both so I could boot either way, BIOS or UEFI. But most of that is from my newer drives in my older BIOS only system that I thought I might move drive to a new UEFI system. Then I used bios_grub for BIOS boot, but could later install in UEFI on new system.

Is your system UEFI or BIOS?
If UEFI you can install in either UEFI or BIOS, but UEFI is probably better.
If BIOS make sure AHCI is on for trim to work.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

