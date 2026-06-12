---
title: "Increasing size of hard disk space allocated for unbuntu filesystem"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by Alfalfa1234 on 2010-01-04
Hello,
   
  I recently installed Bio-Linux 5.0 as a dual boot system with XP for some bioinformatics applications, but I’m having some problems with the amount of disk space which can be allocated specifically for the Ubuntu install.
   
  I partitioned a 250 GB portable hard drive into:
   
  /dev/sdb1: 154.76 GiB (with 30 GiB allocated for Ubuntu)
  /dev/sdb2 : 78.13 GiB
   
  I’ve been using blastclust to analyse some very large data sets, which keeps on crashing due to filesystem running out of disk space.
   
  When I installed Bio-Linux 5.0 from the live cd, the maximum size I could allocate to the install was 30 GiB, and I haven’t been able to find a way to change this.
   
  I’ve tried using System->Administration->Partition Editor using the live cd, and can view / delete the partitions, but I can’t find a way to specifically alter the disk space allocation for Ubuntu.
   
  How do I increase the filesystem size to larger than the current 30 GiB?
   
  [FONT=Arial]Any help would be appreciated[/FONT]

---

### Post by quicknick_26 on 2010-01-04
This is probably a stupid question. When you say "live cd", are you referring to a Bio-linux or Ubuntu live cd or are you referring to the GPartEd live cd? I had issues modifying the partitions with GPartEd from within Ubuntu myself (maybe because the partition was mounted). If you insert a GPartEd boot disc while the computer is booting, you should have no problems.

---

### Post by Alfalfa1234 on 2010-01-05
Thanks for the reply,
   
  I originally tried running Ubuntu from the live cd, so I could access the partitions onto which the filesystem from the previous install was loaded, then ran GPartEd to try and change the filesystem space allocation.
   
  After your answer I also downloaded the GPartED .iso in order to make a boot disc, which I then ran.
   
  Unfortunately with both options I can see the partitions, used and free space, delete or create new partitions. This shows that there is 30 GiB (Ubnutu system files) of used space and 120 GiB of free space on the first partition.
   
  I still can’t find a way to increase the 30 GiB hard disk space allocation for the Ubnutu install using GParted?

---

### Post by drs305 on 2010-01-05
I wrote the following guide for a slightly different reason, but the way to expand the Ubuntu partition remains the same:

[ Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

The first part doesn't apply to you so you can go to the section "Some basic options" followed by the step-by-step guide.

---

### Post by dariush_03 on 2010-01-05
I once had the same problem in "gparted" although I started it from the live cd.

  I still can’t find a way to increase the 30 GiB hard disk space allocation for the Ubnutu install using GParted?[/quote]

It should be possible to resize a partition with "gparted" as long as your preferred partition is not mounted. So you should first unmount your harddrive.

---

### Post by Prendi on 2010-01-05
Sound to me as if your ubuntu resides not directly on a partition, but in a 30GB disk image on your /dev/sdb1 . If that's the case, gparted can't help you. Instead you'll need to increase the size of said file with random data (e.g. "dd if=/dev/zero of=<the ubuntu image file> bs=1G count=30 oflag=append" to increase the file size by another 30 gigabytes. Be aware that mistakes (mine or yours) here can corrupt the whole ubuntu system.) Afterwards, you'll need to use the tools for your file system type to resize the file system inside the image. For ext2/3/4 that would be resize2fs. 

For ext2/3/4, you'll need to have exclusive access to the file, e.g. you should boot from a live cd to execute these steps. For other file systems, it may actually be necessary for the file system to be mounted during resizing.

---

