---
title: "Upgrading Windows 10 removed my ubuntu dual boot partition"
date: 2015-08-29
forum: Installation &amp; Upgrades
---

### Post by kengcc on 2015-08-29
Hi,

Here's my previous setup:
- Windows 7 & Ubuntu dual boot, default is to boot into Windows 7

Yesterday I ran Windows 10 upgrade, it upgraded windows 10 fine, but Windows seem to change the boot/partition information.
I manually ran USB ubuntu and ran boot-repair's recommended repair, boot-repair seems to fix it by changing the boot into MBR.

Here's the pastbin information: [http://paste2.org/c6Az7PIj](http://paste2.org/c6Az7PIj)
From the partition info, I suspect /dev/sda4 is where my Ubuntu sits, but it now shows as "unallocated", how do I fix it so I can boot into Ubuntu again?

---

### Post by Bucky Ball on 2015-08-29
You have no Linux install anywhere. It has been completely removed. sda4 is an extended partition, a container, not a partition as such. It holds logical partitions/drives, in this case sda5, which is a /swap partition. That belongs to your Ubuntu install, but there isn't a Ubuntu install there that I can see.

You have all NTFS partitions, none of which could be Ubuntu as it doesn't install to an NTFS partition, only EXT partitions, none of which you have.

---

### Post by kengcc on 2015-08-29
Thanks Bucky Ball, looks like either Windows 10 or the boot-repair's "recommended repair" modified my Ubuntu partition already? I'm sure my ubuntu /root is somewhere in the remaining 50+Gb location because I've been using is for over 2 years... is there anyway I can recover the partition?

---

### Post by efflandt on 2015-08-29
I am sure that I have seen other posts about this. It would have been nice to have fdisk data from before you upgraded to Win10. The data for your Linux partition is likely still there, just not in the partition table. Note that there is a gap between where sda4 (extended partition) starts, and your swap partition.```

/dev/sda4         144,367,614   250,068,991   105,701,378   5 Extended
/dev/sda5         241,817,600   250,068,991     8,251,392  82 Linux swap / Solaris
```So I think people have used testdisk to find it.

I had a problem long ago when installing 64-bit WinXP Pro beta messed up my partition table even though I installed it to an existing partition. Although, it was somewhat different in that 64-bit XP beta changed my drive CHS from its odd 240 heads to 255 heads (along with changed cylinders, sectors), so nothing would boot (not even the just installed XP beta). But I had only glanced at (not saved) fdisk data from before that. So I had to do the math to change cylinders, heads, sectors back to 240 heads with fdisk and some trial & error reconstructing the partition table. But in the end I got everything to work. Then while installing SuSE at the time I noticed that the numbers looked odd because it wanted to do the same thing (change number of heads), so I just told it NO, use the existing partition that I already set up for it. 64-bit WinXP beta expired and has been removed, but that early Athlon64 3200+ (2 GHz) still has its original WinXP Home (never reinstalled), along with 32 and 64-bit Ubuntu 10.04.

---

### Post by Bucky Ball on 2015-08-29
Testdisk and Photorec. Here you go:

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

Testdisk description:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Photorec description:
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by kengcc on 2015-08-29
Thanks all, I managed to recover all lost partitions using:
1. Boot into Live USB linux
2. Use Testdisk to recover all partitions
3. Use boot-repair to restore damaged Grub

---

### Post by Bucky Ball on 2015-08-29
Excellent news. Please mark thread as solved. See first link in my signature for how. :)

---

