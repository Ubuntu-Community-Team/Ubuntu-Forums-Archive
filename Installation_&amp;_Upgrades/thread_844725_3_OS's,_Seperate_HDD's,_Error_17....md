---
title: "3 OS's, Seperate HDD's, Error 17..."
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by jkapernicus on 2008-06-29
In my system I have 4 HDD's. On one I have Vista, on the 2nd is my storage, on the 3rd I have another OS, and on the 4th I just installed Hardy. 

For the install method I chose guided use whole disk and selected the disk I wanted to use. Install went fine, I rebooted and set BIOS to boot new Ubuntu HDD first. Now, I get grub to bring me to the partition selection menu, I select the 1st option 2.something (generic), and I get Error 17...cannot boot selected partition (something like that). The only option that will boot is the last option "Vista Bootloader".

I want to have Ubuntu on its own drive and be able to either boot to it or Vista? What am I doing wrong? I have tried all the solutions I can find but nothing works.

---

### Post by Pumalite on 2008-06-29
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
Do you have a mix of SATA and IDE?

---

### Post by jkapernicus on 2008-06-30
I am using all SATA drives. I just found a post similar to mine and one suggested that the user type fdisk -l in the terminal. So I did that via live CD and this is what I got..

[I][Disk /dev/sda: 300.0 GB, 300090728448 bytes

255 heads, 63 sectors/track, 36483 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x41c441c4



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       36483   293049666    7  HPFS/NTFS



Disk /dev/sdb: 320.0 GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x5edb5edb



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS



Disk /dev/sdc: 160.0 GB, 160000000000 bytes

255 heads, 63 sectors/track, 19452 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xb75bb75b



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1       18657   149862321   83  Linux

/dev/sdc2           18658       19452     6385837+   5  Extended

/dev/sdc5           18658       19452     6385806   82  Linux swap / Solaris



WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.





Disk /dev/sdd: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00000000



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1               1        9730    78150743+  ee  EFI GPT



Disk /dev/sde: 4009 MB, 4009754624 bytes

16 heads, 32 sectors/track, 15296 cylinders

Units = cylinders of 512 * 512 = 262144 bytes

Disk identifier: 0x00000000



   Device Boot      Start         End      Blocks   Id  System

/dev/sde1               1       15296     3915760    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ ][/I]

the last device is my readyboost flash drive. Does everything look correct in this log?

---

### Post by Pumalite on 2008-06-30
While in the Live CD:
sudo mkdir /media/sdc1
sudo mount -t ext3 /dev/sdc1 /media/sdc1
Post:
cat /media/sdc1/boot/grub/menu.lst

---

