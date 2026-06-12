---
title: "partition hard drive without reformatting"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by superprad on 2006-09-07
Hi:
I have a fedora core 5 running currently. There are no partitions. Its just one full install.
What I would like to do is resize this to create a small partition and install ubuntu to dualboot. I dont want to loose my current FC5 install and end up with a dual boot FC5 and ubuntu.

so basically I currently have

FC5 -> X Gigs

after partiton:

FC5 - > x-y Gigs
ubuntu -> y Gigs

I want to create a small partition 'y' without loosing my FC5 on X and install ubuntu and dual boot. The only thing i'm not sure is how to partition the existing space FC5 occupied without loosing it.

any help is greatly appreciated

---

### Post by orb9220 on 2006-09-07
I think what you want is to bootup with the a liveCD and use gpart to resize.
Then you would end up with an unallocated space at the end which would be used for creating partition for ubuntu.

---

### Post by superprad on 2006-09-07
on I put in the ubuntu cd and booted up. But when I open the qtparted it does'nt allow me to resize the partition. 

this is what it shows on the partition table:

partioion filesystem    size    used       unused   flags
/dev/hda1   ext3      101.35MB 44.97MB    56.98MB    boot
/dev/hda2   unknown   74.43GB    ---        ---       lvm

when I right click on thn hda2 it only gives me either delete or format options...
Is there something i'm missing?

---

### Post by superprad on 2006-09-07
whne i try to resize the partition using gparted on ubuntu live cd it thinks the fc5 partition /dev/hda2 in above post as "unkown" filesystem type. How do i fix this so that Gparted can resize my partition.

---

