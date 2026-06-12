---
title: "growisofs - dual layer burning fails, used to use hdparm"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by emil on 2008-05-05
Hi!


just upgraded my server to 8.04, went without a problem. Until I tried to burn a dual layer dvd iso using growisofs. 


I had some problems with this before and found out that running the following command before burning helped:
```
sudo hdparm -X66 /dev/hdc
```


Now, with Hardy, I noticed that the naming is not hd* any more. Seems all harddrives and optical drives are treated as SATA and the designated name for my DVD burner is now scd0.

But it seems that hdparm won't work any more and my burns fail.


This is how I use growisofs:
```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=1 -Z /dev/scd0=$1
```

It burns for a while but always fails with:
```
 2096824320/7835492352 (26.8%) @2.0x, remaining 29:06 RBU 100.0% UBU  53.1%
:-[ WRITE@LBA=fa1e0h failed with SK=4h/ASC=08h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
```

I've tried different medias but always coasters are produced. Mind, CD's and single layer dvd burn just fine. And it worked flawlessly with DL burns before my distro upgrade. 

Can someone help me out, is there another tool to use that might change the same settings as hdparm? 

Regards

Emil

---

### Post by emil on 2008-05-08
Wow, not a single answer. Has not one person had the same problem and can share??


I bought a new DVD-recorder today, one that connects through SATA instead of IDE. Works perfectly again. 


Guess I'll never find out if the old drive was faulty or if there actually is a problem with IDE burners...

/Emil

---

### Post by bml137 on 2008-05-09
I am having a burner problem as well.  It is different than yours however.  What is similar is that it worked before, and the switch to SATA-emulation has caused it to malfunction.

---

### Post by stumpalump on 2008-08-14
Having exact same problem.

My cd drive is /dev/cdrom1

and hdparm outputs

```
/dev/cdrom1:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Output of  hdparm -X66 /dev/cdrom1
```
/dev/cdrom1:
 setting xfermode to 66 (UltraDMA mode2)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error

```

Any ideas?

---

### Post by cariboo on 2008-08-14
actually linux is converting the drive to sccsi so instead of using dev/cdrom use whatever device it is mapped to. For example on my system /dev/cdrom is linked to /dev/scd0.

Jim

---

### Post by stumpalump on 2008-08-14
> **cariboo907 said:**
> actually linux is converting the drive to sccsi so instead of using dev/cdrom use whatever device it is mapped to. For example on my system /dev/cdrom is linked to /dev/scd0.

Jim

How do I find out where it's mapped to?

---

### Post by rhonaldmoses on 2008-08-27
Hi, I have the same problem for past few month with Ubuntu ever since I upgraded to Hardy heron. Dual Layer disks doesn't burn in any of the DVD burning softwares. Any great ideas to share? Tried most of the device options listed above as well as other forums, it's kind of frustrating.

---

### Post by rhonaldmoses on 2008-08-27
This link might help you:

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/200337](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/200337)

Regards,

---

