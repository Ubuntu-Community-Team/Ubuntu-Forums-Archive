---
title: "Can I just copy / from live cd to back the partition up??"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by e-dard on 2008-05-06
Hi, I am thinking of trying another distribution to test my hardware, although there are no live cd's available.

I was wondering: Since I have my home folder on a seperate partition to my os, would it be ok to just boot up with an ubuntu live cd and copy my entire / partition (with hidden files) to an external drive.  Then format and install my new OS on the partition.  Then, if I want to go back, just reformat and copy the backup / folders etc back. 

I realise I won't copy my mbr, but that's ok as I don't mind having to reinstall grub.

Please be aware, I am referring to just copying the files from nautilus on a live cd rather than anything clever like dd of copying the partition byte for byte.

Would this rather simple idea work??  I wonder because I can't see why it wouldn't??!??

cheers,

e-dard

---

### Post by ChronoSphere on 2008-05-06
It could work, but there are some things to watch out for. For example, the external drive must be ext2 or some permissions will be lost. And you'll have to copy as root or  some files will be skipped.

I think it's better to clone the partition with dd. The only problem is that this will copy the entire partition even if you only have 3GB used. You can use gparted to shrink it to avoid this.

---

