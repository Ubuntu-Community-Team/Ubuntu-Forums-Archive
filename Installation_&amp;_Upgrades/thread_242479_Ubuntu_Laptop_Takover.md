---
title: "Ubuntu Laptop Takover"
date: 2006-08-23
forum: Installation &amp; Upgrades
---

### Post by cspaz on 2006-08-23
Been using Ubuntu exclusively on my laptop for about a week now and just love it.  It currently dual boots into Windows XP, but I'm ready to give Ubuntu the entire hard drive.  What I don't want to do is go through a reinstall now that I've got my current install working like I want it.  So, what's the best way to give Ubuntu the rest of the hard drive without screwing up my current install?  I'm assuming I'm going to use gparted or some partition manager to repartition the current NTFS to ext3 or something, but what mount points should I use?  Has anyone done this before? 

Thanks in advance!

---

### Post by John.Michael.Kane on 2006-08-23
cspaz use the [gparted live-cd]("http://gparted.sourceforge.net/index.php") to edit, and move your space. 

It should allow you to transfer your space to your existing partitions be it swap / home.

---

### Post by cspaz on 2006-08-23
So I'll just delete the NTFS partitions with gparted and add the extra space to my / partition?  I've currently only got 2 partitions, / and swap.  Should I create another partition for /home or just leave it as is?

---

### Post by John.Michael.Kane on 2006-08-23
Yes the gparted live cd will allow you to delete the windows partitions, and allow you move the free space back your current partitions.

---

### Post by cspaz on 2006-08-23
So should I just leave the / and swap partitions or try to add a /home partition?

---

### Post by handaxe on 2006-08-23
Putting /home on another partition is a good idea.  That way you can  re-install if need be and keep your data (with backups made of course!).

I am uncertain, on this point, but search the forums on topic grub to make sure you are not going to incur problems there.  Should be ok but...


cheers,

HA

---

