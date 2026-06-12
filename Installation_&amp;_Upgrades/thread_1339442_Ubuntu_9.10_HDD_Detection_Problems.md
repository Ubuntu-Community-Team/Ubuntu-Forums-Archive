---
title: "Ubuntu 9.10 HDD Detection Problems"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by atr1991 on 2009-11-27
I newly installed windows 7 and after that I tried to install ubuntu 9.10. The installer can't recognize the hard drive that I installed windows 7 on it but it detect my other hard drive. Gparted detects both of hdds and drives also shown in places. I also tried to disconnect the second hard drive but installer can't recognize it again. after that I tried to install ubuntu 9.04 and installer recognized the drive. Any Solutions?


Motherboard : GA-M59SLI-S5
CPU : AMD Athlon 64 X2 5000+
Ram : OCZ 4*512MB 800
VGA : nVidia 7600GS
HDD0 : Smasung SP2504C
HDD1 : WDC WD-5000AADS-0

---

### Post by darkod on 2009-11-27
And wher do you want to install Ubuntu? The installer might not show you the first drive because it's already occupied with Win7 and has no free space. If you want to install Ubuntu on the second drive it doesn't really matter if the installer is not showing you the first one.
Both drives are correctly shown in Places and after the install they will probably both be shown again.

---

### Post by atr1991 on 2009-11-27
It has free space and also unallocated space about 8GB and I want to install it on that unallocated space

---

### Post by darkod on 2009-11-27
OK, boot with the ubuntu cd, select Try Ubuntu option and in terminal run:
sudo fdisk -l (small L)

Copy the results here and maybe we'll figure it out.

---

### Post by atr1991 on 2009-11-27
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dbdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       29341   235573248    7  HPFS/NTFS
/dev/sda3           29342       30401     8514450    5  Extended
/dev/sda5           29342       30401     8514418+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a1287ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488383488    7  HPFS/NTFS

---

### Post by darkod on 2009-11-27
> **atr1991 said:**
> 
Partition 1 does not end on cylinder boundary.


This might be the problem. I think Gparted can repair this but I'm not sure, never needed to use it for that.

---

### Post by atr1991 on 2009-11-27
In GParted I've selected "check" but it said there is no problem. What should I do now?

---

