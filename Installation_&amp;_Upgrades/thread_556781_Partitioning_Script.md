---
title: "Partitioning Script"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by Greslore on 2007-09-21
I am trying to find a way in which I could write a script that would do the following:

1) delete any existing partitions on hard drive
2) create 3 partitions: NTFS, SWAP, EXT3 to a specific size

Can someone steer me in the right direction for this?  I suspect I'll need to create some type of boot cd.  Or is it possible to modify gparted live in some manner to do the above?

---

### Post by ddrichardson on 2007-09-21
Why would you need to do this - not trying to be condecending just wondering why. If it's for creating a default install on multiple machines, then they would need to have the same drive geometry to do this with scripts. That would bely the fact the setting one up then imaging the entire drive would be a more effective way to configure multiple machines.

---

### Post by Greslore on 2007-09-21
Nods, it is ultimately for installing Kubuntu and WinXP on about 30 identical machines.  I tried using Norton Ghost to image all the partitions, but for some reason it didn't work.  GRUB got mangled (easily fixed), as well as the ext3 partition didn't get all the data after I fixed GRUB.  

I decided to just create the partitions on the drives via gparted live, install kubuntu, post config it with all packages, ldap config, and such with scripts, and then just ghost the NTFS with a WinXP image.  I kind of like this better as now I can install kubuntu on any machine.

---

### Post by ddrichardson on 2007-09-22
There are some serious problems with Ghost, especially with ext2/3 - have you tried [System Rescue CD]("http://www.sysresccd.org/Main_Page")? It's a live CD aimed at recovery, but is only a 123 Mb download and includes among other things such as gparted, ntfs-3g and partimage. Incidentaly it will image entire drives or just partitions and even just the MBR.

I've never had any problems with it, and even if you just use it to create an image of a partitioned drive you'd be laughing.

---

