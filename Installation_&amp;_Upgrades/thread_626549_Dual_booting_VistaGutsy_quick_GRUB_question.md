---
title: "Dual booting Vista/Gutsy: quick GRUB question"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by jin psu on 2007-11-29
First post (hooray me).

So I'd like to set up my Dell desktop to dual boot Vista (shipped OS) and Gutsy.  I freed up about 40gigs at the end of the disk (SATA HD), deleted the FAT16 Dell Utility partition at the front of the disk, and extended the Vista partition to the front of the disk (formerly the 2nd partition).  So now my disk looks like this:

   [  -- Vista partition -- ] [ -- unpartitioned --]

The plan is to partition the disk like this:

  [ -- Vista partition -- ] [ -- / partition -- ] [ -- swap -- ] [ -- /home partition -- ]

I'd like to install GRUB to the root ('/') partition and use the Vista boot manager.  However, my partition names are out-of-order with respect to physical location (due to Vista formerly being the 2nd partition).  This is what I mean:

  [ -- Vista partition (sda2) -- ] [ -- / partition (sda1) -- ] [ -- swap -(sda3) -- ] [ -- /home partition (sda4) -- ]

So, even though Vista is at the front of the disk, it's labeled sda2.  Now finally the question; when I specify a location to install the GRUB boot loader, should I select (hd0,1) because '/' is physically the second partition on the first disk *OR* (hd0,0) because '/' is logically the first partition on the first disk due to its name (sda1)?

Thanks!

justin.

---

### Post by logos34 on 2007-11-29
(hd0,0) is what you want...grub will look at the partition table. 

Here's something that might interest you (although you've probably seen it already):
[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

---

### Post by jin psu on 2007-11-29
Thanks, (hd0,0) it is.

Yeah I've seen EasyBCD and am planning on using it to configure the Vista boot manager.  Looks like a slick app (at least on paper).

justin.

---

