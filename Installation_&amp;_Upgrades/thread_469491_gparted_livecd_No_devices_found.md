---
title: "gparted livecd: No devices found"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by treesurf on 2007-06-09
I am attempting to dual boot Vista on top of my Feisty installation.  The first step in this is resizing my Feisty partition.  To do this I tried using the gparted livecd.  Unfortunately something is not quite right as gparted informs me that there are no devices detected, and no partitions appear on the screen.

I tried again using gparted on the Feisty livecd.  This time it detected the partitions, but when I tried to resize a partition it gave an error saying it could not do so.

Do I have a problem with my hard drive?  If so what can I do about it?

---

### Post by koshari on 2007-06-09
i found that the gparted live cd didnt detect my sata drives so i think it may be a udev issue on the gparted live cd.

also i had the ubuntu disk regignise my partitions on my acer which had a preinstalled vista partition,

and again as you said gparted wouldnt resize the partition.

i later found that vista has a built in volume resize feature.
HOWEVER the vista resize feature hosed the vista partition, 

i had to blow the partition away and create some new partitions the size i want and use the acer eRestore function to restore vista to those partitions to make room for linux.

i dont know what would be the best advice to resize the vista partition but due to being a dynamic volume its not streight forward, i would imagine you may need a 3rd party all like acronis to acheive your outcome,  mind you i havnt tried partimage on a vista dynamic partition . but i did use it succesfully to move my existing ubuntu desktop installation from a 10 gig pata drive to a 120gig sata last week.

---

### Post by treesurf on 2007-06-10
Thanks for the advice.

However I'm not trying to resize a Vista partition.  I'm trying to resize my Feisty ext3 partition so that I can fit Vista on the hard drive too.  The gparted live cd doesn't see any partitions at all.

---

### Post by Nanoboy on 2007-06-10
Sorry for needing to point out the obvious - is the new partition u created mounted when you boot with the live CD?  Gparted should see it if it is mounted...

---

### Post by treesurf on 2007-06-10
Yes, when I used the Feisty livecd gparted did detect the partitions. However, when I tried to resize the partition it returned an error and refused to do so.

---

### Post by Nanoboy on 2007-06-10
I've only resized an empty partition.  Resizing a partition with Windows installed on it might be more tricky.  What type of file system is your Vista on?  FAT32 or NTFS?

---

### Post by treesurf on 2007-06-11
OK, so I'll explain again, with some new info.

I have Feisty installed on this hard drive using all available space.  I would like to resize the main ext3 partition, in this case /dev/sda1, so that I can install Vista on a new partition.

Using the Feisty Live CD, I have tried to resize this partition using gparted.  Gparted says that it is unable to accomplish this task and says that the filesystem needs to be checked.  Being kind of a Linux dunce it took me a little while, but I finally figured out how to use fsck and have checked the filesystem with it.   However, gparted still returns the same error and refuses to resize the partition.  

Any suggestions on how I should proceed?

thanks

---

