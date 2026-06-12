---
title: "Win7 + nix sharing a drive for documents: best filesystem?"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by phillips321 on 2010-08-17
Hi guys,

Am currently building a new PC and will be using both ubuntu 10.04 and win7.

I have 2x 320GB drives and 1x 1TB drive.

I plan to use a drive each for the OSs (win7 + nix) and the 1tb for my home partition.

My home partition will store my music, videos, docs, Virtual Machines (note file sizes are sometimes bigger than 4GB!).

What file system should i use? FAT32 will not work because of the large file size of the virtual machines.

What do you recommend?

Cheers in advance

---

### Post by sydbat on 2010-08-17
> **phillips321 said:**
> Hi guys,

Am currently building a new PC and will be using both ubuntu 10.04 and win7.

I have 2x 320GB drives and 1x 1TB drive.

I plan to use a drive each for the OSs (win7 + nix) and the 1tb for my home partition.

My home partition will store my music, videos, docs, Virtual Machines (note file sizes are sometimes bigger than 4GB!).

What file system should i use? FAT32 will not work because of the large file size of the virtual machines.

What do you recommend?

Cheers in advanceNTFS. Ubuntu has had built in NTFS read/write support for quite awhile.

---

### Post by phillips321 on 2010-08-17
I'm well aware that NTFS is read/write but I'm not entirely sure that the performance will be all that good.

Does ubuntu prevent the files from becoming fragmented?
How much of a performance hit will be seen over using a native filesystem such as ext4?
What limitations will I have by using NTFS?

Many thanks

---

### Post by phillips321 on 2010-08-17
Also, will NTFS fully cope with the permissions that nix requires for home partitions?

---

### Post by tommcd on 2010-08-17
> **phillips321 said:**
> 
I plan to use a drive each for the OSs (win7 + nix) and the 1tb for my home partition.

If you want the files to be readable from both Windows and Ubuntu, then your only option is NTFS because Windows will not read linux file systems.
It seems there are ways to enable reading linux file systems from Windows though:
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)
[http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html)
Don't use NTFS for Ubuntu's home partition though. You could mount the 1TB drive as /data or /media/whatever if you want to use NTFS for the 1TB drive. Just install Ubuntu to the 320GB drive as you planned. 
If you were planning to use the 320GB drive as Ubuntu's root partition that is way too much space to use just for Ubuntu's root. Make root about 20GB. The rest of that drive can be Ubuntu's home partition. Make swap at least equal to the amount of memory you have if you plan suspending the system to memory. If you don't plan on doing that then 1GB is plenty for swap.
If you want to use a linux file system for the 1TB drive, go with either ext3 or ext4. Use ext3 for maximum reliability to protect your data. Ext4 is more mature and reliable than it was in older versions of Ubuntu though, so you could use ext4 and be safe with that.
Use ext4 for Ubuntu's root partition. It is the default on the Ubuntu install CD.

---

