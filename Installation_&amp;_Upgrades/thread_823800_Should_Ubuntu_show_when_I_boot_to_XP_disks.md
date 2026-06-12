---
title: "Should Ubuntu show when I boot to XP disks?"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by DrQuincy on 2008-06-09
Hi

I installed Ubuntu and then XP on this machine. Ubuntu works fine but XP is totally trashed and I need to reinstall it. I have no idea how this works but when I boot to the XP disk it gives me the choice of a single 130 GB partition to delete or overwrite. Should the Ubuntu one show here? It says it's an Unknown partition. I ran:

```
sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ccf3cce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       38156   172281060   83  Linux
/dev/sda3           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

```

Is 134206978+ in any way related to 130 GB? I'd like to leave my Ubuntu install untouched as it's taken me ages to get everything how I like it. What is the relevance of the * on boot? It boots to GRUB...

---

### Post by tom66 on 2008-06-09
It might be advisable to partition inside Ubuntu, then install XP in this new partition.

---

### Post by housam on 2008-06-09
Open Gparted and post a screen shot of the image. by this way you'll be sure about the sizes of your partitions.

---

### Post by meierfra. on 2008-06-09
> Should the Ubuntu one show here? It says it's an Unknown partition. 

It should show you an NTFS partition  and  two unknown partitions.

---

### Post by DrQuincy on 2008-06-09
> **meierfra. said:**
> It should show you an NTFS partition  and  two unknown partitions.

That's what I thought. Something has seriously gone wrong with my XP partition. It won't boot (just gets to the loading bar) even in Safe Mode and Command Line. I have tried the diagnostics like CHKDSK and FIXBOOT (or whatever it's called) and none of them will work - it say it has an unrecoverable error. What should I do? :S Can I save this Ubuntu install or should I start over?

---

### Post by meierfra. on 2008-06-09
Follow housam's advice and look at the partition with gparted.  If the Ubuntu partition looks fine, follow tom66's  advice and reformat you Windows Partition with Gparted. Maybe  then your Windows CD will recognize all the partitions.

To install  Gparted:

```
sudo apt-get gparted
```

to run Gparted:  System->Admininstration-Partition Editor 

(or type "gksudo gparted"in a terminal)

---

### Post by DrQuincy on 2008-06-09
thanks so far for the great advice.

Looking at gParted the NTFS partition is indeed ~130 gig. It has an alert sign against it saying it is unreadable; this must be to do with the problem Windows is having booting / repairing. To get the XP CD to recognise it should I delete it or format it. If that latter what do I format it to?

Thsnks again.

---

### Post by meierfra. on 2008-06-09
> Should I delete it or format it. If that latter what do I format it to?
Just format it to "NTFS".  Also make sure it has the boot flag.

---

### Post by DrQuincy on 2008-06-09
NTFS is greyed out. :( It will let me do ext 2/3 and fat16 or 32. What will happen if I delete it?

---

### Post by meierfra. on 2008-06-09
Strange.  Delete it and  then see whether the  Windows CD  recognizes all the partitions.

You might also try the [Gparted LiveCD]("http://gparted.sourceforge.net/"),

---

### Post by DrQuincy on 2008-06-09
Thanks, will do. TBH honest I think something has gone seriously wrong without. LEet's hope deleting it and starting over solves it.

Thanks everyone.

---

