---
title: "Mount hardware RAID 1 drives"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by stickcore on 2011-07-21
Hello, First time user of ubuntu or any linux based OS.
I'm trying to build a NAS currently I have 3x 1TB drives all SATA 6.0GB.
I'm using the HighPoint RocketRAID 620 controller (hardware) to RAID 2 x 1 TB drives at RAID 1. RAID1 array has been made from the bios setting. The other 1TB is installed to the motherboard. 

the issue, how do i mount the RAID array created from the bios?
when I do, sudo fdisk -l I am getting the following:
device          boot         start            end           blocks           ID        system
/dev/sda1       *               1             121392       975076352   83        Linux
/dev/sda2                   121392         121602        1683457       5         Extended
/dev/sda5                   121392         121602        1683456      82         Linux swap / Solaris

What now? How do i mount it to use it? I'm guessing sda2 and sda5 is my RAID1 array?

Any help will be great. THanks!

---

### Post by psusi on 2011-07-21
You seem to have edited the output a bit, there should have been more.  sda is the hard disk that you have installed Ubuntu to, and it has 2 partitions: sda1 holds the system, and sda5 is for swap.

---

### Post by stickcore on 2011-07-21
> **psusi said:**
> You seem to have edited the output a bit, there should have been more.  sda is the hard disk that you have installed Ubuntu to, and it has 2 partitions: sda1 holds the system, and sda5 is for swap.

I didn't edit any output... as a matter of fact, I don't even know how to do that...
All I know is that I have 3x1TB drives... I figured that sba1 is the one that holds ubuntu. not sure what the other sba2 and sba5 is. guessing from the volume size, that is my 2x1TB drives that are attached to my raid controller?

so lost....

---

### Post by tgalati4 on 2011-07-21
It doesn't appear that Ubuntu recognizes your RAID1 array.  It should show up as /dev/sdb1.  You'll have to do some more research on the RocketRAID 620 support in the version of the kernel that you are using.

Swap is put on /dev/sda5 so you can split up your main partition (/dev/sda1).  /dev/sda2 is an extender placeholder since most partitioning schemes only allow 4 primary partitions.  

If you are just building a NAS, I prefer [http://freenas.org](http://freenas.org)

---

