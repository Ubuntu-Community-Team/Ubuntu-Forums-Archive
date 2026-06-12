---
title: "Partitioning and GRUB"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by tmh177 on 2008-06-22
I have tried to install using the CD that was downloaded, when I get to install I get stuck on the partion setup.

I have two drives- one has Vista on it, has well as another Primary Partion, both are divided up equally (8o MB each). The other Drive is a seperate HD for image backups only.

I am trying to use the EasyBCD program, as I located it in another post on the forum. According to documentation, _**I should do manual partition and then tell Grub to load onto its own partition. Will continue after below inf is given:**_

While in partition menu only two items are available one reads as follows:

Guided Rezize SCSI4(0,0,0)Part #2 SDA and freespace 
Dev/SDA2         3.7
Ubuntu          70.8

If guided is used instead of manual, will I still be able to tell Grub where I want it and what step does Grub come in to the install? Also is the 3.7 the swap file size

The other option I get is Manual with the following showing up

Dev/sda1   NFTS (type)  80019 (size) 22400 (used)
Dev/sda2   NFTS (type)  80017 (size)  3200 (used)
Dev/sdb1   NFTS (type) 100253 (size) 68599 (used)

Only one I can use is the Dev/sda2, but when I select and go foward, I get no root systen defined. 

I have done a search and have found out I need to use (ext2?) as filesytem and / as mount-point. 

_**How would I do this to get the 3.7 & 70.8 ratio as in guided; for swap and filesystem (pre-suming the 3.7 is the swap file size?**_

Just want to find best method to use for the EasyBCD and Grub, as per above info.


A complete Newbie to Ubuntu, I hope this is not confusing to read?

TMH177

---

