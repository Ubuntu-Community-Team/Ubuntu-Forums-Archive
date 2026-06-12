---
title: "Kubuntu 6.10 partition table problem"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by jonathannewell on 2007-01-12
Hi all,

I am a total noob.  I burn the ISO Kubuntu 6.10 to disk and booted in my dell laptop.  I started install and to use built-in partition tool to select unused space for new partition.  I then realize I need a second partion for swap.  So I canel out of the installation.   Even though I cancelled out of installation, my machine now blue screens when I try to boot windows.  I have to select 'last know good boot' every time I boot now.  (this boots the machine sucessfully)

Seems that windows is failing on the CRCDISK check. 

Also partition Magic 8.0 reports error #117 'Partitions drive letter cannot be identified'

Why did the installer change my disk when I cancelled out of install?
How do I fix?

TIA
-Jonathan

---

### Post by Sense on 2007-01-13
How far were you in the install?  
If you're letting the install program choose how to divide the free space, it's automaticaly making a swap partition.

---

