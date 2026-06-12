---
title: "Hard drive not visible to Ubuntu installer (Acer Aspire 3)"
date: 2020-03-03
forum: Installation &amp; Upgrades
---

### Post by sbayl33 on 2020-03-03
I'm trying to install Ubuntu 19.10 onto an Acer Aspire 3. I'm having the same problems described in this post on the Acer forums here: [https://community.acer.com/en/discussion/579165/aspire-3-fail-installing-ubuntu](https://community.acer.com/en/discussion/579165/aspire-3-fail-installing-ubuntu), I can get into the live environment from a bootable USB but when I try to install Ubuntu, my laptop's hard drive is not visible to the installer, only the bootable USB that the live environment is running from. Consensus seems to be, from that post and a couple of others, that this is probably due the BIOS SATA mode. The default SATA mode is Optane without RAID and the option to change it is initially hidden. Shift + S in the 'Main' tab of the BIOS menu reveals the SATA mode option and I changed it to AHCI. Booted back into the live environment and still nothing. GParted also can't detect the hard drive and it doesn't show up when I run sudo fdisk -l. This is what gets returned when I run sudo fdisk -l through the terminal: 

> 
Disk /dev/loop0: 1.87 GiB, 1982222336 bytes, 3871528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 89.13 MiB, 93454336 bytes, 182528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.52 MiB, 57151488 bytes, 111624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 149.93 MiB, 157192192 bytes, 307016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 14.76 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 44.18 MiB, 46325760 bytes, 90480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.62 GiB, 15682240512 bytes, 30629376 sectors
Disk model: Cruzer Blade    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x002557e0

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 30629375 30627328 14.6G  c W95 FAT32 (LBA)

Any ideas? Let me know if you need any more information.

---

