---
title: "How to preserve RAID from previous install?"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by HarvesterOfBeer on 2008-03-04
I have a existing CentOS 5 linux machine with a primary OS drive (IDE), and 4 SATA disks set up in a software RAID 5 (extfs3). For a variety of reasons, I'm going to install Gutsy on the machine, replacing CentOS. I don't care about preserving anything on the primary disk, but I need to maintain the RAID.

Can somebody please point me to an FAQ or clue me in on how to move the existing RAID set intact?

Thanks!

---

### Post by dstew on 2008-03-04
You can use the mdadm program "Assemble" function to create a RAID device on a new Ubuntu install out of a previously assembled RAID. [This site]("http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html") talks about it (second page). The main difference is that you can install mdadm in Ubuntu using Synaptic. No need to compile it from source or use an RPM package.

---

