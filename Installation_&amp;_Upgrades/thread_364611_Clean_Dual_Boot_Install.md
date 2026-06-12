---
title: "Clean Dual Boot Install"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by truck87bp on 2007-02-18
1. Back up your data.
2. Back up all of your data (take a 2nd look)
3. Get Gparted, this program works great and I'm a noob. Get "Burn4Fre" for making ISO burn files under windows, it has a drop down for BURN ISO's and works great. (slick)
4. Ubuntu only likes 4 partitions per drive. I just accepted that but you can have multi hard drives.
5. Linux and Windows **can both read Fat32**...this is good news...they can share your data.
6. Partitions ( I'm using 2 hard drives, 1-400 gig and 1-200 gig secondary)
    Windows XP partition ...... 60 gig     NTFS
    2nd partition...................275 gigs  Fat32
    3rd partition................... 60 gigs   Ext3
    4th partition................... 5 gig       Swap

    2nd Drive
    2-100 gig both Fat32 partitions  (Note: In Gparted, you can change to the 2nd HD in the upper right hand corner to partition the 2nd drive.


7. Install XP on the NTFS drive (duh) and update it to service pak 2 (SP2) (about 3+ hours of work)
8. Install Ubuntu 6.10 on the Ext3. It will want to format the Ext3 and the Swap file...read carefully and make sure you are selecting the right partitions. (about 20 minutes to install Ubuntu from the disk and about 37 minutes to do the automatic updates. (so sweet)

8. Retun all of your backed up data to the Fat32 partitions at your convience.

Have fun as I (NOOB) am doing.....:lolflag: :) :popcorn:

---

