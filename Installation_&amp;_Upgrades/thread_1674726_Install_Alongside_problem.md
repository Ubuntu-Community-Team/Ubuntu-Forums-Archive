---
title: "Install Alongside problem"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by Thunderhawk60 on 2011-01-24
Hi everyone, I'm a newbie and have an installation issue.I can't install alongside my Windows 7.It only presents 2 options during installation: Use entire disk and wipe out Windows or Manually specify the partitions. It doesn't give the option of install alongside Windows. :(

The same thing was happening with the Linux Mint Installer when I tried it out.I have freed up space on my C drive(windows 7 installed here) and have 40GB of free space.I then defragmented it and tried but still no option of install alongside windows....

I also have an entire free partition(E drive - around 80 GB of free space).Right Now I have installed it inside windows using WUBI but I want it to run alongside for better performance.

Any Help would be appreciated..

---

### Post by Rubi1200 on 2011-01-24
Hi and welcome to the forums :)

From a LiveCD, run the following commands in the terminal:

```
sudo parted -l

sudo fdisk -lu
```Post the output back here please.

---

### Post by Elfy on 2011-01-24
We need to see what partitions you have - and how they're set up.

Please run this command from a terminal on the livecd - terminal can be found in apps - accessories

```
sudo fdisk -l
```

---

### Post by presence1960 on 2011-01-24
> **Thunderhawk60 said:**
> 
Any Help would be appreciated..

Post the output from the terminal commands that have been requested please.

---

### Post by Thunderhawk60 on 2011-01-24
OK I ran the command sudo fdisk -l and got:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44639f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        7650    61337600    7  HPFS/NTFS
/dev/sda3            7650       19123    92160000    7  HPFS/NTFS
/dev/sda4           19123       30402    90596352    7  HPFS/NTFS


and with sudo parted -l :

Model: ATA WDC WD2500AAJS-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   62.9GB  62.8GB  primary  ntfs
 3      62.9GB  157GB   94.4GB  primary  ntfs
 4      157GB   250GB   92.8GB  primary  ntfs

and with sudo fdisk -lu :

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44639f42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   122882047    61337600    7  HPFS/NTFS
/dev/sda3       122882048   307202047    92160000    7  HPFS/NTFS
/dev/sda4       307202048   488394751    90596352    7  HPFS/NTFS

I have 3 drives C(Windows 7 installed), D(just has a few PC Games for Windows) and E(Completely free - Ubuntu installed inside Windows here...)

---

### Post by presence1960 on 2011-01-24
You already have 4 primary partitions. You are maxxed out. You can have 3 primary and 1 extended partition or 4 primary. Inside the extended you can have as many logical partitions that you wish- the only limitation being how much space you allocate for the extended partition.

You must remove a primary partition to install another OS.

Edit : you said E: is empty. Then delete that using gparted from the Live CD and install to that unallocated space for ubuntu.

---

### Post by Thunderhawk60 on 2011-01-25
Got it! Installed alongside windows successfully.
Thanks alot for the assistance.:p

---

### Post by presence1960 on 2011-01-25
> **Thunderhawk60 said:**
> Got it! Installed alongside windows successfully.
Thanks alot for the assistance.:p

Glad you got it working. Enjoy ubuntu.

---

