---
title: "Ubuntu 14.04 can not detect windows 8.1"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by john196 on 2014-04-20
Hi,

My laptop is a aspire 5560g with AMD A6-3400m cpu. It used to run windows 7 and ubuntu 12.04 with no problem. 

Now I re-installed windows 8.1 in legacy mode using mbr partition method.

I boot into ubuntu liveCD and try to start the installation but can not see option "install alongside with windows".

The options are to "erase everything and install fresh" or "Something else" (which goes into a disk partition interface where the disk looks empty. I cannot do install this way because it feels like it will erase the entire windows installation.)

sudo parted -l
ubuntu@ubuntu:~$ sudo parted -l
```

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? No                                                                

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

```

gdisk -l /dev/sba
```

GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 1
Disk /dev/sda: 1250263728 sectors, 596.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8EA71E3A-A002-4BD0-AAF4-D55C27E1A3AE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1250263694
Partitions will be aligned on 2048-sector boundaries
Total free space is 6765 sectors (3.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          718847   350.0 MiB   0700  Microsoft basic data
   2          718848       272279551   129.5 GiB   0700  Microsoft basic data
   3       272279552      1250258943   466.3 GiB   0700  Microsoft basic data

```




What should i do now?

---

### Post by john196 on 2014-04-20
bump

---

### Post by Jim_Kajder on 2014-04-20
Curious. Have you tried going into Windows 8.1 disk manager and reducing the size of your windows partition to make a space for Linux, and then see if the installer can find the free space? As I recall, Ubuntu needs about 5 GB to install, personally I would go larger than that so you have room for applications.

---

### Post by john196 on 2014-04-20
Thanks for the advice~

But ubuntu still doesn't see that new partition. I am guessing it's the same reason it doesn't see other windows partition.

---

### Post by Luke M on 2014-04-20
The disk has both MBR and GPT partition tables (the Windows installer didn't erase the old GPT table like it should have), and maybe the ubuntu installer is arbitrarily picking the GPT one. So I would suggest erasing the bogus GPT table. gdisk can do it (note: don't erase the MBR!):

[http://askubuntu.com/questions/211477/how-to-remove-gpt-from-hdd](http://askubuntu.com/questions/211477/how-to-remove-gpt-from-hdd)

---

### Post by oldfred on 2014-04-20
From fixparts you can easily remove the extra gpt data. Windows just does not correctly convert to MBR from gpt.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Or convert Windows DVD to flash drive and update it for UEFI install. Then you can have UEFI and gpt partitioning, if you want.

---

