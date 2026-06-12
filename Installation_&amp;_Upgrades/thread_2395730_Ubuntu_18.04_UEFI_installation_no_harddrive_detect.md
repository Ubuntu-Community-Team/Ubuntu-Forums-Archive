---
title: "Ubuntu 18.04 UEFI installation no harddrive detected when installing."
date: 2018-07-05
forum: Installation &amp; Upgrades
---

### Post by naruto.itachi on 2018-07-05
Hello guys, I am trying to install Ubuntu 18.04 along with windows.
My system specs: 
[LIST]
[*]3 TB hard drive
[*]32 GB ram
[*]Gtx 1070 8gb
[*]intel optane memory 32gb
[*]Asrock mother board
[/LIST]

I have disabled fast boot and also created a partition for ubuntu.
Windows is installed in UEFI mode, so I am trying to do the same in Ubuntu. The problem is I am not able to see hard disk when installing ubuntu. I did go to try ubuntu and did fdisk -l 

root@ubuntu:/home/ubuntu# fdisk -l
Disk /dev/loop0: 1.5 GiB, 1564921856 bytes, 3056488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: EE70993B-4640-4899-B142-18B89DD16CB8

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1023999    1021952  499M Windows recovery environment
/dev/sda2  1024000    1228799     204800  100M EFI System
/dev/sda3  1228800    1261567      32768   16M Microsoft reserved
/dev/sda4  1261568 2959845375 2958583808  1.4T Microsoft basic data


Disk /dev/sdb: 14.8 GiB, 15854469120 bytes, 30965760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x550f2a26

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3172287 3172288  1.5G  0 Empty
/dev/sdb2       3138412 3143147    4736  2.3M ef EFI (FAT-12/16/32)

I could only see 1.4 tb which I have for windows. I'm not able to see 1.4tb that I have partitioned. I don't know what to do. I am very new to Linux and I don't want to get discouraged with this error. I have spend a day already reading out different forms. Can someone please help me.

---

### Post by yancek on 2018-07-05
fdisk doesn't output accurate information on gpt partitioned drive so try the command below and if you don't understand it, post it here.  Do this booted from the Ubuntu install usb.

```
sudo gdisk -l /dev/sda
```

How did you create a partition for Ubuntu?  Not much point doing it from windows and you are usually better off shrinking the largest windows partition to create free/unasllocated space for Ubuntu.  It would also be a good idea for  you to read through the Ubuntu documentation on dual bootin UEFI with windows 10, link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by naruto.itachi on 2018-07-05
Thanks for the response. I did disk partition in windows, I shrieked volume of one disk to 1.5 tb and I have 1.5 tb of unallocated space.
Quick update: 
[LIST=1]
[*]sudo apt-get remove dmraid 
[/LIST]
[FONT=inherit]I did this and I could install Ubuntu but it is not getting loaded. But when I disable RAID mode ubuntu is getting loaded but windows is failing to load.  


I am having an additional problem which I didn't mention I am attaching url for the error. So much appreciate your help.
[URL="https://ibb.co/dp6kNJ"]https://ibb.co/dp6kNJ

GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): EE70993B-4640-4899-B142-18B89DD16CB8
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860528590
Partitions will be aligned on 2048-sector boundaries
Total free space is 2477 sectors (1.2 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1023999   499.0 MiB   2700  Basic data partition
   2         1024000         1228799   100.0 MiB   EF00  EFI system partition
   3         1228800         1261567   16.0 MiB    0C01  Microsoft reserved ...
   4         1261568      2959845375   1.4 TiB     0700  Basic data partition
   5      2959845376      3545782271   279.4 GiB   8300  
   6      3545782272      3577032703   14.9 GiB    8200  
   7      3577032704      4162969599   279.4 GiB   8300  
   8      4162969600      5860528127   809.5 GiB   8300  

[/URL][/FONT]

---

### Post by larry2311 on 2018-07-05
There are issues with "Intel RST" RAID mode as opposed to AHCI mode with the Linux Kernel. An install of dual booting can be achieved with mdadm manual configuration, but is problematic, as a kindest description. At least until "Intel RST" is fully supported in the kernel.

So, may I suggest you have a look the links below for further info and understanding a way forward for a dual install with conversion to AHCI mode.

[https://askubuntu.com/questions/999934/trouble-installing-ubuntu-for-dual-boot-along-with-win-10-the-installation-type](https://askubuntu.com/questions/999934/trouble-installing-ubuntu-for-dual-boot-along-with-win-10-the-installation-type)

[https://forums.lenovo.com/t5/Linux-Discussion/Trying-to-dualboot-with-Ubuntu-but-SSD-not-recognized-by-Ubuntu/td-p/4013450](https://forums.lenovo.com/t5/Linux-Discussion/Trying-to-dualboot-with-Ubuntu-but-SSD-not-recognized-by-Ubuntu/td-p/4013450)

[https://forums.linuxmint.com/viewtopic.php?t=268174](https://forums.linuxmint.com/viewtopic.php?t=268174)

This is using dmraid, which is being depricated, so moving forward is mdadm. Again, converting to AHCI  boot is simpler at the moment.
[https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID](https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID)

---

### Post by oldfred on 2018-07-06
In addition to having drives in AHCI mode, Asrock has some ports as Intel and some as Asmedia.
You cannot use the Asmedia ports for any drive, even a DVD or you will have issues.

       Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564)

---

