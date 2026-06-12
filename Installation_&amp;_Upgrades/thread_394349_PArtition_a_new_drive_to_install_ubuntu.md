---
title: "PArtition a new drive to install ubuntu"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by numerical on 2007-03-26
Thanks everyone for your help !

**My goal is to be able to select which operating system I want to choose from when i boot up** :

First of course I am trying to install ubuntu on a new partition .I have XP on my main and only partition right now . So as it stands I havent created and new partitions yet.  I have booted up the UBUNGU OS and I opened the
GPARTED partition tool - and I am ready to resize my NTFS partition (60gig)and free space(30gig)for the EXT3 partition (set primary boot) and as well as a small SWAP parition (1gig) .My question is should I select these settings and then revert to the INSTALL button on the desktop or should i EXECUTE the partition from within Gparted?


Can anybody walkme through what step I need to take from here to finalize the new partition(s) and installation of ubuntu os?

Thanks 
Numbers

Lattitude D810,2gig Pentium M ,x600ATI mobilty w/128mb video card,2gig SODIMM SDRR RAM,60gig harddrive.

---

### Post by simonn on 2007-03-26
Sorry, but I cannot really help you with the partitioning and resizing (have been winfree for a few years.. and am being just a little lazy :)). However, I would suggest that you have a seperate partition for your /home directory. This makes upgrading, moving/experimenting with distributions a lot easier and safer.

IMHO/E something like the following where X is any disk space left:

7-8Gb /
1Gb Swap
XGb /home

---

### Post by mikewhatever on 2007-03-26
Exit gparted and hit the install button on the desktop. The installation process will begin, during which you'll be asked to resize the Windows partition. It is outlined here:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

