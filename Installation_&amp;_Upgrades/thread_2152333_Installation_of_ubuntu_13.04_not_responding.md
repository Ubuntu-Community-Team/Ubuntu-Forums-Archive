---
title: "Installation of ubuntu 13.04 not responding"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by ahmed11ber on 2013-06-07
Hi

I have installed ubuntu 13.04 64bits on laptop hp pavilion g6 in dual boot with winodows7 but when it finished installing it said that I have to restart my computer When I restart my laptop and removed my liveCD it started directly  with windows without giving me to choice wich operating system i choose I don't know why every thing was all right I want a help to co;plete my installation

here is my partitions
da: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  67.1MB  66.1MB  primary   ntfs            boot
 2      67.1MB  151GB   151GB   primary   ntfs
 3      151GB   360GB   210GB   primary   ntfs
 4      360GB   500GB   140GB   extended
 5      360GB   390GB   30.0GB  logical   ext4
 6      390GB   394GB   3999MB  logical   linux-swap(v1)
 7      394GB   500GB   106GB   logical   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$

---

### Post by ahmed11ber on 2013-06-07
when I run from terminal sudo fdisk -l here is the response

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd5f2444c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      131071       64512    7  HPFS/NTFS/exFAT
/dev/sda2          131072   294088703   146978816    7  HPFS/NTFS/exFAT
/dev/sda3       294088704   703698943   204805120    7  HPFS/NTFS/exFAT
/dev/sda4       703700990   976771071   136535041    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       703700992   762292223    29295616   83  Linux
/dev/sda6       762294272   770105343     3905536   82  Linux swap / Solaris
/dev/sda7       770107392   976771071   103331840   83  Linux

---

### Post by ahmed11ber on 2013-06-07
I have downloaded boot-repair and the URL is:[http://paste.ubuntu.com/5742276/](http://paste.ubuntu.com/5742276/)
I want a help to have  the options for running Windows 7 or Ubuntu 13.04 in my computer

---

### Post by ahmed11ber on 2013-06-07
Hello
 
I have succefully installed Ubuntu 13.04 64 bits alongside with my windows7, when I reboot my machine there no option to run my ubuntu 13.04, it reboots directly with windows 7 although ubuntu is in my machine.In order to solve the problem I download boot repair I made the report info and the pasting URL is.: [http://paste.ubuntu.com/5742276/](http://paste.ubuntu.com/5742276/)
 
And I click on the recommanded repair it did lot of things and the message dispalyed is this attached to this email.
 
Please I want a help to run Ubuntu 13.04 alongside with my windows7
 
thanks

---

### Post by oldfred on 2013-06-07
You do not have the grub2 boot loader installed to the MBR of sda. If you run the suggested repair it will automatically install it and let you dual boot.

Since you have Windows in BIOS with MBR(msdos) partitioning, you should boot live installer in BIOS mode also, not UEFI mode.

---

