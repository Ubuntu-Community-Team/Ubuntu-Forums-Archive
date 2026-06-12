---
title: "Grub 21"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by dc02linux on 2007-02-20
Hi i'm new to UBUNTU,  but i'm having troubles allready.

I have a ASUS P5AD2 motherboard and two RAID 0 HDD's

To install UBUNTU I bought a new SATA HDD and install ubuntu on that HDD.

When I tried to start after install I got the " GRUB ERROR 21"

Any one can help me fixing it ?

---

### Post by tgalati4 on 2007-02-22
Could be one of several things:

Bad hard disk.  Did you exercise the disk before installing Ubuntu?  Many large capacity disks require break-in before they run properly.  It looks like grub can't find it's stage 1 operating system.

BIOS settings.  Look in the BIOS and turn on or off drive translation settings.  I assume that these are large SATA drives and the motherboard may be treating them differently.

Did you load or update Windows on the first disk?  Windows does not recognize any other operating system and it will kill grub--happily.  Very happily.

Set up a grub boot floppy (search the forum: grub floppy) and try to boot Ubuntu via floppy.

Swap disk drives so that the Ubuntu disk is in the "first" disk slot.  Use the Live CD and select boot from first drive.

I'm confused, you have two drives set up as RAID 0, did you add a third drive for Ubuntu or is Ubuntu loaded on the second drive?

I don't have experience with setting up grub on a RAID drive.  Others will have to weigh in on how to set it up properly.

Welcome to the community and keep the faith,

Terry

---

### Post by rsambuca on 2007-02-22
Actually grub error 21 is a stage 2 error (picky, I know!).

From the grub manual> Error 21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

Looks like you will have to check your drive settings in the bios.

---

### Post by tgalati4 on 2007-02-22
You are correct.  Stage two looks for the /boot/grub/menu.lst and interprets it.   Perhaps the root (hd0,0) line is malformed.

At the grub menu>  (note the response to the following)

root  (hd0,0)                                     first drive, first partition
root  (hd0,1)                                     second drive, second partition
root  (hd1,0)                                     second drive, first partition
root  (hd1,1)                                     second drive, second partition

You want the one that says valid ext2 or ext3 partition
boot

edit your /boot/grub/menu.lst to reflect the correct root partition.


then you should be good to go.

---

### Post by dc02linux on 2007-02-22
Thank you guys.
 I will try that out and let you know the result.

---

### Post by confused57 on 2007-02-22
> **dc02linux said:**
> Thank you guys.
 I will try that out and let you know the result.

You might want to boot up the desktop live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L"

this will show how Ubuntu recognizes your hard drive partitions

Also, at the bootup grub menu, you can highlight the entry to boot Ubuntu, press "e" to edit, then experiment with different locations for root as tgalati4 has mentioned, then press "b" to boot...any change you make here is temporary, but you can make it permanent in your /boot/grub/menu.lst if you find and entry that works.

---

