---
title: "cannot acess free space in hdd"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by mannu177 on 2008-10-13
I m new to ubuntu and i tried installing installing it in my laptop lenovo Y410, i already had windows vista but it had some problems of compatibility with sound and wireless so i deleted the partition for ubuntu from windows and merged it with my D drive in windows since then i have not been able to acess the free space i even tried installing ubuntu again and that can also not acess it, it shows unsable memory please can you helo me...

---

### Post by cariboo on 2008-10-13
Could you post the output of:

```
sudo fdisk -l
```

Posting question about memory or a question with the word memory it, most of us assume you mean ram. Think of it this way a hard drive is permanent storage while ram is temporary storage.

Jim

---

### Post by mannu177 on 2008-10-13
thanks..
I got a way to correct it 
i booted with ubuntu live cd and started with expert mode 
and then i could acess the disk and formatted it to use

but later  had same problem again
the result 

ubuntu@ubuntu:~$ fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

can any1 help

---

