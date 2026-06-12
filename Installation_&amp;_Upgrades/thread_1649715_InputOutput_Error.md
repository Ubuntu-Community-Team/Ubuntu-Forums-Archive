---
title: "Input/Output Error"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by Spitfire777 on 2010-12-20
Hi,

I want to install Xubuntu 10.10 x64, but it does not work. 
While copying data the setup tells me about an Input/Output error, but i don't think there are hardware errors.

The environment:

AMD Phenom II 1055t 6x2,8 Ghz
2x 2gb ram
Hitachi 1TB hard drive
Two partitions: 1st for Windows 7 Ultimate (NTFS), 2nd for my Data (NTFS)

So I decreased the size of the data partition and created two new partitions beside the Win7 partition and the data partition. The first is ext4-journal (20gb) the second is Swap (4gb).
I've done that all by the Xubuntu setup.

I've downloaded the image from the german mirror (TU Chemniz) and checked the integrety via SHA1. Checksum was correct. 

I also checked the data after burning.

---

### Post by mr clark25 on 2010-12-20
> **Spitfire777 said:**
> 
I also checked the data after burning.

with what method?

---

### Post by Spitfire777 on 2010-12-21
The way CDBurnerXP does, CRC i guess.
I also used the "check cd/dvd" feature of the desktop cd.

---

### Post by Rubi1200 on 2010-12-21
If possible, post the exact error please.

Thanks.

---

### Post by psusi on 2010-12-21
> **Rubi1200 said:**
> If possible, post the exact error please.

Thanks.

This, and also open the disk utility on the livecd and look at the SMART status of the drive.  Pay specific attention to the reallocated, pending, and offline_uncorrectable numbers.

---

