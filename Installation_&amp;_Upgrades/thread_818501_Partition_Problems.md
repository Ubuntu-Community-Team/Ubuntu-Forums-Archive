---
title: "Partition Problems"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by magical_tom on 2008-06-04
I, have got an ubuntu 8.04 disk, and I put it in, tried it out, And clicked install. I went through to stages, untill it asked me about the partition. I chose the origional windows 68% and linux 22%, or whatever it is. It wouldn't work, telling me there wasnt enough space. i went back onto windows, cleared a load of stuff out and went back. This time, it did work. I filled in my details and was one step away from installing. Me, being me, i accidentally clicked cancel. Now i have a partition on the disk, and if i try and install Ubuntu again, it wont let me. Any help?

---

### Post by avtolle on 2008-06-04
> **magical_tom said:**
> I, have got an ubuntu 8.04 disk, and I put it in, tried it out, And clicked install. I went through to stages, untill it asked me about the partition. I chose the origional windows 68% and linux 22%, or whatever it is. It wouldn't work, telling me there wasnt enough space. i went back onto windows, cleared a load of stuff out and went back. This time, it did work. I filled in my details and was one step away from installing. Me, being me, i accidentally clicked cancel. Now i have a partition on the disk, and if i try and install Ubuntu again, it wont let me. Any help?
Someone may well have a better answer; I hope so; but it seems to me that you will need to reformat that partition, then try to install Ubuntu on it.

---

### Post by VMC on 2008-06-04
That's exactly what I would do. Start over. 

As far as the percent used, its the percent of the total drive space. Run gparted and it will show how much gigabytes used instead.

---

### Post by magical_tom on 2008-06-04
Ok, i have delited the unused partition, However now when i am on the install ubuntu part, i get to the partitions section, and there is no longer an option as to how many percent you want to partition. I think this is because It doesnt recognise the partition/memory due to it being NTFS.

---

### Post by avtolle on 2008-06-04
Are you selecting guided use largest available space or something like that? It would seem that the other partition would be recognized by gparted, and it would just use the available space created by deleting the partition you had created for Ubuntu, where it would install. I'm assuming, of course, that you want to use the remainder of the HDD for the Ubuntu installation.

---

### Post by magical_tom on 2008-06-13
I dont really know, but before, it gave me the option of setting the partition size, among other options, however now that option is gone.

---

### Post by zvacet on 2008-06-13
Download [gparted live cd]("http://gparted.sourceforge.net/").With it you can shrink your existing win partition if you want(defragmet it few times before you shrink) or if you have two partitions you can delete one and leave it as unallocated space.You can format unallocated space as ext3 or you can format it during installation.

---

