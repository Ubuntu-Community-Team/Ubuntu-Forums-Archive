---
title: "GCC help"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by Xcelerate on 2006-05-24
I seem to have this long stream of problems.

Firstly, I want to install Linux in a new partition.  So I downloaded the NTFS-progs and ran the live CD.  Unfortunately, it says I need to compile the thing and that I don't have GCC.  Also, GCC seems to be 34 megabytes, which would take forever to download on dial-up.

In addition to that, I am trying to install winmodem support, which I also need GCC to compile, and I am trying to install Captive-NTFS, which requires FUSE (which doesn't seem to be on the live CD), which also requires GCC to compile the thing.

Any ideas?  Maybe if GCC is included on the installed version of Ubuntu, someone might know how to repartition without all that work.

Thanks.

---

### Post by an.echte.trilingue on 2006-05-24
I would recommend you use the SLAX liveCD to do all your pre-installation administrative work.  

Just read the documentation on how to add modules to the CD, then at qtparted, fuse, maybe darksun, and you will be good to go.

It is easy and you will only have to download another 250 MB or so.

---

### Post by Sef on 2006-05-25
> Firstly, I want to install Linux in a new partition. So I downloaded the NTFS-progs and ran the live CD. Unfortunately, it says I need to compile the thing and that I don't have GCC. Also, GCC seems to be 34 megabytes, which would take forever to download on dial-up.

In addition to that, I am trying to install winmodem support, which I also need GCC to compile, and I am trying to install Captive-NTFS, which requires FUSE (which doesn't seem to be on the live CD), which also requires GCC to compile the thing.

Any ideas? Maybe if GCC is included on the installed version of Ubuntu, someone might know how to repartition without all that work.


Don't install GNU/Linux to NTFS, you are just asking for problems.   

1) Check that the Live CD works ok with your computer.

2) Either use GParted on the Live CD to create a ext3 or reiferfs partition or download GParted and burn it to a cd and create ext3 or reiferfs partition.

[GParted]("http://gparted.sourceforge.net/livecd.php")

---

