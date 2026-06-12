---
title: "Can't Mount Large FAT32 Partition...Any suggestions?"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by FaytlND on 2006-03-17
So I just managed to install on a fresh 160 GB drive, which is actually the third drive on the computer.  The other HD contains a Windows XP install that I still would like to use.  I partitioned the new drive as follows: 10 GB for /home, 9.5 for root, 0.5 for swap, and 140 GB as a FAT32 partition.  My goal was to be able to use the 140 GB partition as a crossover between Ubuntu and XP.  

I have successfully mounted my XP NTFS drive, and have had no problems using it.  However, I am having considerable problem with the large FAT32 partition.  I try to mount it, but this is what I get:

patrick@ubuntu:~$ sudo mount /dev/hdd6 /media/f
mount: wrong fs type, bad option, bad superblock on /dev/hdd6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

patrick@ubuntu:~$ dmesg | tail
[4295321.080000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4295321.080000] apm: disabled on user request.
[4295505.195000] ibm_acpi: ec object not found
[4295510.584000] cdrom: open failed.
[4296653.079000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4296792.601000] FAT: bogus sectors per cluster 0
[4296792.601000] VFS: Can't find a valid FAT filesystem on dev hdd6.

Here is the FDISK from the drive:
patrick@ubuntu:~$ sudo fdisk -l /dev/hdd

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1            1166       19457   146930490    5  Extended
/dev/hdd2   *           1        1165     9357831   83  Linux
/dev/hdd5           18243       19457     9759487+  83  Linux
/dev/hdd6            1221       18241   136721151    b  W95 FAT32
/dev/hdd7            1166        1219      433692   82  Linux swap / Solaris

Furthermore, when I load up windows, it says the new partition is not formatted, and I can't use it.

Any suggestions would be greatly appreciated.  Thanks in advance!

-Patrick

---

### Post by LordBug on 2006-03-17
Can XP read it ok?

Try 'sudo mount -t vfat /dev/hdd6 /media/f' and see what happens.

---

