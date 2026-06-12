---
title: "HDD not detection"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by Talz on 2007-01-24
ok 
well im trying to install 6.10
my comps specs are

monitor: 37" hdtv
cpu: amd athlon 3800 (64bit)
intel motherboard
graphics: intergrated ati reaseon express 400
1 gig of ram
2 hdd's both are SATA 
   180 gig maxtor thatis my windows drive
   250 western didital that i just bought it only has 160 gigs of partioned space trying to get ubuntu on the other 90
entergrated enthernet

ok  now my problem
 while the cd boots live fine and all
but when i try to install it doesnt pick up either of my HD's
which isquiet frustrating D;
i dont see any errors  just plain old dont see em

not sure i got all the info needed , if not then just ask and i shall supply 

thanks for your time be watching this thread for a while   really trying to get ubuntu up tonight D;

---

### Post by housam on 2007-01-24
Boot from the live CD. Open the terminal and post the out come of the following code:```
sudo fdisk -l
```

Or use the SYSTEM >> ADMIN. >> Gnome partition editor ( Gparted ) to check your partitions.

---

### Post by Talz on 2007-01-24
ok attached the photos from my camera of what the conel said

wasnt sure if that was a pipe command after the dash or a L  so i tried both

the partition manager isnt detecting either of my Hard drives

---

### Post by Talz on 2007-01-24
i downloaded the alternate x64 install cd
got to the disk detection and asked me which driver to use

i tried them ALL
only one that did anything was cloop   which was asking for table values o.O and even i know that woulda nuked my hd's clean

im really puzzled D;  cause i knwo there both attached and working properly otherwise i wouldnt be able to post D;

---

### Post by housam on 2007-01-24
Ok, Try to use the SYSTEM >> ADMIN. >> Gnome partition editor ( Gparted ) to check if the partitioning tool can detect it or not.

---

### Post by Talz on 2007-01-24
partition editor doesnt detect anything either D;
even refreshed it

---

