---
title: "LTS Install Resized NTFS Partition"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by thedrickster on 2011-07-19
Hello - I am relatively new to Ubuntu and last night decided to "downgrade" from 11.04 to 10.04 LTS. I backed up some data to the NTFS partition and deleted the ext4 & linux swap partition, leaving me with 20GB of unused space in which I intended to install 10.04.

I chose the automatic partition handling, installing along side a windows installation. Much to my surprise when the install finished 1) the GB partion which I intend to use was still unallocated and 2) the 800 GB NTFS partition that I had no intention of touching had 360GB carved out by Ubunutu.

This is absolutely unacceptable behavior on the part of the installer. Can anyone shed light on whether I missed something in the install steps or whether this is typical of the Ubuntu installer, taking portions of an NTFS partition without user input?

Thanks.

---

### Post by cipherboy_loc on 2011-07-19
Usually, when I install allong side Windows, I set it to manual partitioning and specify where I want my Ubuntu partition(s). I don't trust the automatic partitioning scheme with my Windows partitions.

Do you want to smash the Ubuntu down into the 20GB partition, or are you content with it as it is?

Cipherboy

---

### Post by thedrickster on 2011-07-19
Hello - In retrospect, I certainly should have used the manual functionality. The only reason that I used the automatic partitioning was that it worked so well when installing 10.10 & 11.04.

I had intended to smash Ubuntu into the 20GB as I use the 800GB NTFS partition for media & document storage. I am resizing/moving partitions as we speak using gParted...giving Ubuntu 100GB and reclaiming the confiscated GBs and yet unallocated 20GB for NTFS....fingers crossed.

---

### Post by dino99 on 2011-07-19
how you should set it:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

