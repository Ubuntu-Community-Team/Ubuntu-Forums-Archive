---
title: "Wrong Stride in dmraid"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by rianlu on 2008-03-14
Okay for starters I have a sony vaio vgn-ar270g with 2x120 gig seagate hd, and an intel softraid controler setup as raid0 with a 128 stride size.  I have windows vista installed on one partition and another partition for who knows what on the array.  I shrunk the windows partition to give myself space to install Ubuntu(7.1) and have been able to instal dmraid and it recognizes my array but gives the wrong stride size, 256 instead of 128.  i can use fdisk to create the partitions on the empty space and then parted to format them and they show up correctly in parted but they dont show up in /dev/mapper only the root volume shows up there.  is there any way to change the stride size in dmraid?  I think this is why its not reading the partition table correctly, i want to get this working so I can dual-boot,  I thought of using mdadm but I just can't figure out if it will read my existing array or not I may give it a shot though.  Any help on this is appreciated.

Rusty

btw.  i ran dmraid -ay -dddd -vvvv and it showed that dmraid didnt see the existing partions.

---

### Post by rianlu on 2008-03-15
bump(really want ot get this working any help is appreciated)

oh and mdadm shows no valid superblocks is there any way to create those without loseing data?

---

### Post by rianlu on 2008-03-15
Sorry for posting so recently after bumping but after exhausting myself last night and passing out i forgot that the metadata that dmraid is reading and displays after using the dmraid -n command shows a stride size of 256 and the number of strips supports that yet my controller in th bios shows that the stide is 128 not 256 and shows a dif number of total stripes....... this is really starting to get to me I was wondering if I can edit the metadata somehow and then reactivate the array to see if that fixes the prob without losing any data thanx!!!!!

---

