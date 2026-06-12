---
title: "boot partition"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-09-29
Hi,


1) why is it said that on older systems the /boot partition must reside completely below cylinder 1023 ?

2) i have read in a book that many administrators put an ext2 file system on boot partition because the data on it do not change frequently enough to justify the added overhead of the ext3 journal ?

how valid is this claim ?

---

### Post by Partyboi2 on 2008-09-29
>  1) why is it said that on older systems the /boot partition must reside completely below cylinder 1023 ?

I cam across this explanation 
> The                   partition that holds /boot must be                   located entirely below cylinder 1023.  If the partition                   holding /boot straddles cylinder 1023,                   you may face a situation where GRUB and LILO will work                   initially (because all the necessary information is below                   cylinder 1023) but will fail if a new kernel is to be loaded                   and that kernel resides above cylinder 1023.                 

---

### Post by Herman on 2008-09-29
> 1) why is it said that on older systems the /boot partition must reside completely below cylinder 1023 ?The idea is to restrict the area of the hard disk where the Linux kernel can be located to the area that is addressable by the BIOS.
This has to do with the 8.45 GB Standard INIT13 limitation (CHS 1024x256x512), in BIOSes made before about the late 1990s. 

Refer: [Large Disk How-to, Booting]("http://www.win.tue.nl/%7Eaeb/linux/Large-Disk-5.html")

Here is a great explanation of what happens, [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543)

There are other BIOS/Hard drive limits too, 
33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                       137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)
I have never seen any problems booting with the 33.8 GB limit, but I have seen a few 137 GB limit problems.

With modern computers, built within the last eight years or so, you should not need a separate /boot partition unless you are doing something special like installing in an encryped file system or using RAID or something like that.
> 2) i have read in a book that many administrators put an ext2 file system on boot partition because the data on it do not change frequently enough to justify the added overhead of the ext3 journal ?

how valid is this claim ?     If you are installing in a very small hard disk there is a small savings in hard disk space to be gained by only using ext2 instead of ext3.
Remember, it wasn't all that long ago when an 8 GB hard disk was considered very large. The original hard disk in my old 'Book PC was 6 GB and I dual booted Windows 98 and Ubuntu Warty Warthog in 3.0 GB each.  Now we are used to 80 GB or 160 GB hard disks and even 500 GB hard disks and larger are available!
By modern standards, with the huge hard disks most people have now, the saving is not noticeable at all. I think that claim is out of date unless you are installing in a USB flash memory or something like that and every bit of disk space counts. (Just my personal opinion), but then you would be better off to use reiserfs anyway. There is a 6% space savings with reiserfs compared with ext2 and it is around *eight to fifteen times*   faster than ext2 when handling files smaller than one k in size. Even flash memories these days are getting quite large.

Regards, Herman :D

---

