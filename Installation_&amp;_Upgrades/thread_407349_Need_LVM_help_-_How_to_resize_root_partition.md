---
title: "Need LVM help - How to resize root partition"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by fable on 2007-04-12
I have a P4 system running Ubuntu 6.0.6 and a single 20GB hard disk.  This primary master drive is /dev/hda.  LVM was enabled when I first install ubuntu into the system.  Everything is running fine.  This PC is my Linux/Ubuntu learning system.  

I want to learn more about LVM by adding a second hard disk and extend the logical volume size.

I got an old 800MB hard disk.  I installed it as a primary slave drive into the PC.  This drive is now /dev/hdb.

I used fdisk to deleted the old partition, add a new partition and changed the system id to 8e.

I created the physical volume and add the physical volume to the VG, 

At this point I am stuck because my original primary master 20G hard drive only has two partitions, i.e. root and swap_1.  All my file systems are in root.  Although the 800MB disk space from hdb is free, I cannot add the space to the root partition.  unmount root

My understanding is to add the disk space I have to unmount the partition and then resize.  Since I have everything in root, I cannot unmount the root partition and then resize.

Before I do something stupid to the file systems, I am hoping to get some advice on how can I add the free disk space to root.  Alternatively, how do I re-arrange the file systems to increase the disk space.

If I am successful in learning how to add a 800MB, my plan is to use the knowledge learn to add a larger disk into the system in the near future.

The following is pv, lv and vg scan of my system after I added hdb:

root@ubuntu:/# ls
bin          dev     initrd.img      media  root  tmp           vmlinuz
boot         etc     initrd.img.old  mnt    sbin  usplash_fifo  vmlinuz.old
cdrom        home    lib             opt    srv   usr
debootstrap  initrd  lost+found      proc   sys   var
root@ubuntu:/# pvscan
  PV /dev/hda5   VG Ubuntu   lvm2 [18.84 GB / 0    free]
  PV /dev/hdb1   VG Ubuntu   lvm2 [812.00 MB / 812.00 MB free]
  Total: 2 [19.64 GB] / in use: 2 [19.64 GB] / in no VG: 0 [0   ]
root@ubuntu:/# vgs
  VG     #PV #LV #SN Attr   VSize  VFree
  Ubuntu   2   2   0 wz--n- 19.64G 812.00M
root@ubuntu:/# lvsAny advice will be highly appreciated.
  LV     VG     Attr   LSize   Origin Snap%  Move Log Copy%
  root   Ubuntu -wi-ao  18.05G
  swap_1 Ubuntu -wi-ao 816.00M
root@ubuntu:/# pvs
  PV         VG     Fmt  Attr PSize   PFree
  /dev/hda5  Ubuntu lvm2 a-    18.84G      0
  /dev/hdb1  Ubuntu lvm2 a-   812.00M 812.00M
root@ubuntu:/#

Any advice will be highly appreciated.  :D

---

### Post by Jongi on 2007-04-12
An aside: I find that it is always better to put output between code tags. It makes it easier to read as it presents in the form it would on the screen.

If I am reading the output correctly, you have a volume group Ubuntu which has logical volumes root and swap. From the looks of it you have already extended the volumge group Ubuntu to include /dev/hdb1. I am also at this point going to assume that your partitions are ext3.

It is then a case of following [the instructions in the HOWTO](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html). 

You will note that for ext2/3, the volume has to be unmounted. I would then suggest doing this using a LiveCD which has LVM capabilities. I know that I have in the past manipulated LVM partitions by loading my Kubuntu Breezy LiveCD, installing the LVM tools and then resize/delete etc.

---

### Post by fable on 2007-04-12
Yes, I should have use code tag.  I'll remember to use it for my next post.

You are right that I have done all the LVM steps up to including /dev/hdb1 into VG.  I am still learning.  This is the first time I went through these LVM steps.  I am hoping I did the steps correctly.

I am stuck at the point where I have the resize the file system to use up the new free disk spaces in VG.  Standard Ubunutu installation only has the root and swap partitions, in other words, all my file systems are in root.  My initial plan is to find a way to rezie the root to use the new free disk space in VG.

I looked at the "How to" as you suggested.  The steps in the "How to" requires unmounting the file system that will be resized.  In other words, following the steps I would have to unmount the root file system.  This is the point I am stuck because my system won't allow me to unmount root.  Are there some tricks to unmount root, rezie and mount it again?

I am downloading the Kubuntu alternate live CD as you suggested.  My understanding is the alternate live CD has the LVM tools.  I hope the LVM tool in the live CD will allow me to resize root VG to use up the free disk space.

:D

---

### Post by fable on 2007-04-12
I downloaded Ubuntu live CD.  What LVM tools can I install to resize the root partition?

After I booted from Live CD, I started GParted.  In GParted I can see the following:

/dev/hda (19540MB)
/dev/hdb (814MB)
/dev/mapper/Ubuntu-swap_1 (816MB)
/dev/mapper/Ubuntu-root (18473MB)
/dev/mapper/casper-snapshot (2040MB)
/dev/mapper/casper-cow (2040MB)

Can I use GParted to resize root?

:confused:

---

### Post by davemc on 2007-04-20
Consider this.

Should you succeed in resizing your lvm to span two drives, you will be twice as vulnerable to a drive failure and total data loss, since if any member drive of a span set fails, all data is lost.

Given that an 800Mb drive has to be ancient, you are setting yourself up for keeerunch and more disappointment.

I'd suggest you _reduce_ the size of root, to create some free space on your primary drive.

Then use the free space and your 800mb drive to create a non-root partition and span drive set that you can lvcreate, mount, unmount, copy, delete at will.

Even better is to install VMWare, install another Ubuntu in that, and create as many virtual ide and scsi drives as you like in order to learn about LVM.

---

### Post by fable on 2007-05-02
I agreed with your point regarding using LVM will be "twice as vulnerable".  I will look into re-sizing the root partition and also learn how to move /home to a separate logical volume outside /root.

I searched in the Ubuntu Live CD and did not find a LVM too that I can use to re-size /root.  Did I overlook something?  Does anyone know the name of the software in Live CD for LVM management?

---

