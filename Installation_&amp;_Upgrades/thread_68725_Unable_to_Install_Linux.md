---
title: "Unable to Install Linux"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by dabster on 2005-09-24
i recently tried installing a Ubuntu 64 on my AMD sempron 64 computer....
I already had 3 Primary partitions ( I know that's too much) and 1 Extended, And one of the logical drives I installed Ubuntu using Automatic Partitioning.....
But at 6% it gave an error, Some debootstrap error and also that installer returned with error 1 and cannot continue....

After that my Win XP was gone which I managed to recover by changing the Boot flags as Grub was not Installed....

Has anybody come across with same error...
Please help me out...
I hve tried Ubuntu live CD And it is really good....

Help me out.
-- 
dabster

---

### Post by dabster on 2005-09-24
Yeah the error comes when some package debootstrap is being installed...
I googled and found something  here [http://packages.debian.org/stable/admin/debootstrap](http://packages.debian.org/stable/admin/debootstrap)    

While installing this package only I got the error.....
Any Linux geek, plz help me out to sort this problem...
 :???:

---

### Post by bullraiser on 2005-09-30
Hi, 

 I was too finding this problem and somehow overcome it by again reinstalling it other install boot CD. But, then stuck up with some package installation error during base configuration.

 Could someone know, why this happens?

Cheers --

---

### Post by taygan on 2005-10-19
enable dma on your cd drive:

alt-f2 (f3? can't remember) before install packages, try hdparm -d 1 /dev/sda (or whatever your cd drive is) alt-f1 (?) back to the install screen.

Sorry about the lack of details, I've had mucho install problems and went back to hoary.

---

