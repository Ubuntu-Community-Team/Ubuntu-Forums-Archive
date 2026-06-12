---
title: "form Ubuntu to Xubuntu keeping home"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by tommpogg on 2011-08-25
Hi

I would like to switch from Ubuntu 10.10 to another distro (probably Xubuntu 11.04).
My home directory is stored in a dedicated partition and I would like to keep data and info stored in it.

Can I intall the new OS keeping my old home directory (and its content)?
Once the new OS has been installed, how can I restore my home directory?

Yhank you

---

### Post by zvacet on 2011-08-25
If you have separate home partition then your data/files will bwe safe during install.**Just do not format home partition.**If your home is on same partition as /root then you can do upgrade to Natty and then switch desktop.Read [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by tommpogg on 2011-08-25
Since I would like to perform a clean resintallation, I was wandering how to set my home direcotry once the OS has been installed.
Is there a way to do it during installation?

---

### Post by tommpogg on 2011-09-05
Another question: supposing that I want to install two or more Linux systems (e.g. Xubuntu and Fedora), can I use the same home directory for each OS?

All right, I have found the answer I need [here]("http://ubuntuforums.org/showthread.php?t=1157599").
I'm still looking for a way to set up my home directory during installation.

---

### Post by zvacet on 2011-09-11
Let say that your files are on safe place.During installation you will get to the partition stage.Then you can make separate home.Use manual way to partition.Your partitioning table can look like this

1. root=10Gb                                                mountpoint /
2.swap=~2GB
3.home= rest of free space                                  mountpoint /home

---

### Post by tommpogg on 2011-09-12
> **zvacet said:**
> Let say that your files are on safe place.During installation you will get to the partition stage.Then you can make separate home.Use manual way to partition.Your partitioning table can look like this

1. root=10Gb                                                mountpoint /
2.swap=~2GB
3.home= rest of free space                                  mountpoint /home

I agree, but in this way I will format my home directory.
What I would like to do is reinstall the OS while keeping an** already existing** home directory.

---

### Post by mastablasta on 2011-09-12
> **tommpogg said:**
> What I would like to do is reinstall the OS while keeping an** already existing** home directory.
 
 
reinstall overwrites the disk. the only option would be to create a new partition on current driver and move home files there then link it and thus create a separate home partition.
 
for example: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by tommpogg on 2011-09-12
> **mastablasta said:**
> reinstall overwrites the disk. the only option would be to create a new partition on current driver and move home files there then link it and thus create a separate home partition.
 
for example: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

All right. At least now I know that that I can't keep my home directory.
Thanks for the link. It might be useful.

---

