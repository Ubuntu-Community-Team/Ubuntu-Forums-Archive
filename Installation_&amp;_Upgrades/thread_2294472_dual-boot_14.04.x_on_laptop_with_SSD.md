---
title: "dual-boot 14.04.x on laptop with SSD"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2015-09-11
I have a [System 76 _Kudu Pro_]("https://system76.com/laptops/kudu") with 120G of SSD (and 2x 1TB spinners).  It came with nothing installed on the SSD (it boots from the 1st spinner at [FONT=courier new]/dev/sda[/FONT] with 14.04 factory installed and since upgraded to current).   The SSD is [FONT=courier new]/dev/sdb[/FONT].  I am using [FONT=courier new]/dev/sdc[/FONT] as a repository of my old files (uses most of the 1TB).  I am thinking of doing a fresh install of 14.04.3 LTS on the SSD.  that would make a dual-boot with both systems being Ubuntu 14.04.x (_i have no need for any other OS_).  **has anyone done this kind of thing before?**  **any suggestions** (besides not formatting anything on [FONT=courier new]/dev/sda[/FONT] or [FONT=courier new]/dev/sdc[/FONT])**?**  as a disabled person, killing the laptop would be a bad thing for me.  _yes_, i do make backups of [FONT=courier new]/dev/sda[/FONT] to an [external drive (2TB)]("http://www.bhphotovideo.com/c/product/983293-REG/western_digital_wdbmwv0020bbk_nesn_2tb_my_passport_ultra.html").  i want to be sure it gets any drivers needed for the Kudu Pro (user interface) before i try to boot it.

---

### Post by Dennis N on 2015-09-11
There is no problem with having two 14.04 systems being installed on the same computer. I and many others have done it. They could even be of the same release.

Since there is no Windows installed, you have a relatively easy time of it. It's important to know how the system on sda was installed - UEFI or BIOS to describe how to proceed and what to expect.

---

### Post by oldfred on 2015-09-11
It looks new enough that it could be UEFI.
Post this to confirm:
sudo parted -l

If UEFI drives need to be gpt partitioned. And best to have the ESP - efi system partition on each drive. But grub does not correctly install to second drive with UEFI. My second & third test installs of Ubuntu on sdb overwrote the /EFI/ubuntu folder on sda, even when using Something Else and specifying grub boot loader to be installed to sdb's ESP. Installer even said installing grub to sdb but overwrote my sda. I quickly learned to backup my ESP on sda, but if same version of grub, the only difference is the tiny configfile grub in /EFI/ubuntu that has the UUID of the actual grub.cfg in your install.

---

### Post by Dennis N on 2015-09-11
I use this little test to see if a system is installed in uefi mode:

In terminal: 
```
ls -dl /boot/efi
```

If system was installed in UEFI mode:

```
dmn@Sydney:~$ ls -dl /boot/efi
drwxr-xr-x 3 root root 4096 Dec 31  1969 /boot/efi
```

If system was _not_ Installed in UEFI mode:

```
dmn@Daphne:~$ ls -dl /boot/efi
ls: cannot access /boot/efi: No such file or directory
```

Is it foolproof? Or not?

I am thinking parted can be ambiguous as a UEFI detector? Case in point:

```
dmn@Roxanne:~$ sudo parted -l
[sudo] password for dmn: 
Model: ATA WDC WD7500BPVX-2 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  84.9MB  83.9MB  fat32                 boot
 2      84.9MB  87.0MB  2097kB                        bios_grub
 3      87.0MB  63.0GB  62.9GB  ext4
 4      63.0GB  86.1GB  23.1GB  ext4
 5      86.1GB  90.3GB  4194MB  linux-swap(v1)
 6      90.3GB  113GB   23.1GB  ext4
 7      113GB   136GB   23.1GB  ext4
 8      136GB   159GB   23.1GB  ext4
 9      159GB   183GB   23.1GB  ext4
10      183GB   206GB   23.1GB  ext4
11      206GB   229GB   23.1GB  ext4
12      229GB   252GB   23.1GB  ext4
13      252GB   275GB   23.1GB  ext4
14      275GB   298GB   23.1GB  ext4

```

How can we tell?

ON the other hand, I think GPT partition table with proper EFI system partition and no bios_grub flagged partition => UEFI with certainty?

---

### Post by Skaperen on 2015-09-12
```
laptop2/root /root 3# ls -dl /boot/efi
ls: cannot access /boot/efi: No such file or directory
laptop2/root /root 4# 

```
```
laptop2/root /root 4# parted -l
Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  996GB   996GB   primary  ext4            boot
 2      996GB   1000GB  4295MB  primary  linux-swap(v1)


Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  120GB  120GB  ext4         primary


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB  ext4         primary


Model: WD My Passport 0748 (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
121     17.4kB  2097kB  2080kB
120     2097kB  4194kB  2097kB                     bios_grub
 1      4194kB  537MB   533MB   ext2
 2      537MB   8590MB  8053MB
10      8590MB  17.2GB  8590MB
11      17.2GB  30.1GB  12.9GB
12      30.1GB  42.9GB  12.9GB
20      42.9GB  51.5GB  8590MB
21      51.5GB  64.4GB  12.9GB
22      64.4GB  77.3GB  12.9GB
30      77.3GB  85.9GB  8590MB
31      85.9GB  98.8GB  12.9GB
32      98.8GB  112GB   12.9GB
40      112GB   120GB   8590MB
41      120GB   133GB   12.9GB
42      133GB   146GB   12.9GB
50      146GB   155GB   8590MB
51      155GB   168GB   12.9GB
52      168GB   180GB   12.9GB
60      180GB   189GB   8590MB
61      189GB   202GB   12.9GB
62      202GB   215GB   12.9GB
70      215GB   223GB   8590MB
71      223GB   236GB   12.9GB
72      236GB   249GB   12.9GB
80      249GB   258GB   8590MB
81      258GB   271GB   12.9GB
82      271GB   283GB   12.9GB
90      283GB   292GB   8590MB
91      292GB   305GB   12.9GB
92      305GB   318GB   12.9GB
 8      318GB   326GB   8590MB
 9      326GB   1947GB  1620GB  btrfs
100     1947GB  1990GB  42.9GB
101     1990GB  1998GB  8590MB
102     1999GB  2000GB  537MB
103     2000GB  2000GB  537MB
127     2000GB  2000GB  253MB
128     2000GB  2000GB  512B


Model: SD  (sd/mmc)
Disk /dev/mmcblk0: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  32.0GB  32.0GB  primary  ext2


laptop2/root /root 5# 

```
/dev/sdd is my backup drive.  backups are in /dev/sdd9.  i may try to put a bootable system on it later.

that last one is the 32GB SD card/slot.  i have a 2nd 32GB card not in the slot and a 3rd 4GB card.  but the laptop won't boot from it:(

---

### Post by Dennis N on 2015-09-12
Looks like an easy job. From your display, existing installation is not in UEFI mode. So new install should not be in UEFI mode either.

Do you plan to: 

a) continue using the existing Ubuntu grub menu and add the new install on sdb to it, or 
b) do you plan to use the SSD to boot from?

---

### Post by Dennis N on 2015-09-12
Since I need to log out, I will add this: You need to do a little work on the SSD. You need to have a little partition (1-2 MB), unformatted, with a bios_grub flag. It is partition 2 in my display in #4. (You won't need the FAT 32 partition with the boot flag - it's for UEFI.) Even if I planned to continue booting to sda, I believe you need it or grub will not install to sdb at all (see par. 3). You would also then be able to boot to sdb through the one time boot option at startup, or switch the boot drive if you decide later to boot from the SSD.

To do this, I would delete the existing 120 GB partition, them make the partition described above, then another partition for the OS. You can do this first with gparted before using the installer if you want - I usually do.

When installing from the Ubuntu installer, choose "Something Else" in the "Preparing to Install" screen. to get to the partition selector/editor screen where you select the drive and partition to install to. On the bottom, it's important to install GRUB to sdb.

When you reboot, computer will still boot to the old OS on sda (unless you changed to sdb in the firmware) and you need to run sudo update-grub to add the new OS to the existing grub menu.

---

### Post by iulian X on 2015-09-12
> **Skaperen said:**
>   **has anyone done this kind of thing before?**  **any suggestions** (besides not formatting anything on [FONT=courier new]/dev/sda[/FONT] or [FONT=courier new]/dev/sdc[/FONT])**?**  as a disabled person,** killing the laptop would be a bad thing for me**.  _yes_, i do make backups of [FONT=courier new]/dev/sda[/FONT] to an [external drive (2TB)]("http://www.bhphotovideo.com/c/product/983293-REG/western_digital_wdbmwv0020bbk_nesn_2tb_my_passport_ultra.html").  i want to be sure it gets any drivers needed for the Kudu Pro (user interface) before i try to boot it.

Did you leave some free space on the SSD for over-provisioning ?

[http://www.kingston.com/us/ssd/overprovisioning](http://www.kingston.com/us/ssd/overprovisioning)

PS: I am using a SSD but i also have a 500 GB Hard drive.
On the SSD i have Ubuntu Mate and on the Hard drive another Ubuntu Mate + Ubuntu 14.04 with Gnome Clasic Desktop.

When i start my pc i can choose between those 3 Ubuntu instalation.

---

### Post by Skaperen on 2015-09-15
the SSD is currently empty.

i am thinking to use the SSD most of the time, and use the hard drive install to pre-test upgrades to make sure things keep working.  i upgrade regularly (daily on weekdays) and backup weekly (USB 3.0 2TB harddrive).

i want to be sure i have something that works in case an upgrade breaks.  so i would upgrade the SSD regularly and upgrade the hard drive later.  i would look into replicating the SSD to the hard drive so it is a genuine backup so my config changes are more easily copied.  i have had an upgrade break before.

---

### Post by oldfred on 2015-09-15
My system is UEFI, but I also included a bios_grub partition so I could install in BIOS mode.
My SSD & HDD using gpt partitioning.

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  efi
   2         1026048         1030143   2.0 MiB     EF02  
   3         1030144        52229362   24.4 GiB    8300  trusty
   4       246163456       250068991   1.9 GiB     8200  
   5       236079104       246163455   4.8 GiB     8300  iso_ssd
   6        52230144       103429362   24.4 GiB    8300  

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1025484   499.7 MiB   EF00  EFI System Partition
   2         1026048         1030143   2.0 MiB     EF02  
   3         1030144        52229362   24.4 GiB    8300  vivid
   4        52230144       871430143   390.6 GiB   8300  data
   5       871430144       929863679   27.9 GiB    8300  backup
   6      1939193856      1953523711   6.8 GiB     8300  iso_hdd
   7      1392136192      1939193855   260.9 GiB   8300  homerun
   8      1388230656      1392136191   1.9 GiB     8200  
   9       929863680       978692095   23.3 GiB    8300  wily_b
  10       978692096      1029891314   24.4 GiB    8300  trusty_3

```

I was testing homerun on this PC, but it will now become more data or other installs or ?.

---

### Post by Dennis N on 2015-09-15
> **oldfred said:**
> My system is UEFI, but I also included a bios_grub partition so I could install in BIOS mode.
My SSD & HDD using gpt partitioning.


@oldfred,

I have a question for you. My gdisk -l output (below) doesn't show labels like yours. How do you get them to display? Here, partitions 1,3, and 4 have labels that display in gparted and file manager, but not in gdisk or parted.

```
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  
   2         1050624        82970623   39.1 GiB    8300  
   3        82970624        91162623   3.9 GiB     8200  
   4        91162624       304154623   101.6 GiB   8300  

```

---

### Post by oldfred on 2015-09-15
With gpt there are two labels. I add them to both places and try to be consistent.

In Disks you can add both labels.
Click on the little gears for more actions under the partition screen.
Edit filesystem & edit partition.

I am not sure which tools use which label when showing labels.

I was not totally consistent.

In Disks, filesystem shows efi for sdb1
from sudo blkid
```
/dev/sdb1: LABEL="efi" UUID="68CD-3368" TYPE="vfat" 
```

 from sudo gdisk -l /dev/sdb
In Disks partition shows EFI System Partition for sdb1
```
 Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1025484   499.7 MiB   EF00  EFI System Partition


```

---

### Post by Dennis N on 2015-09-15
O.K. thanks. I will hit the books tonight and see what I can learn about this.

---

### Post by Dennis N on 2015-09-20
> With gpt there are two labels. I add them to both places and try to be consistent. In Disks you can add both labels.

In addition to Disks, I find that the newer gparted (version 0.23.0) can create partition names in gpt partitioning, _and_ file system labels. The current version (0.19.0) cannot do partition names, so this is a welcome new feature.

---

