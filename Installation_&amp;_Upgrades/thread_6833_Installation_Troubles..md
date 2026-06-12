---
title: "Installation Troubles."
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by Infatuated_iPod on 2004-12-01
i am trying to install ubuntu on my laptop,.. but i get this error message at the partitinoning screen... 

> 

PARTITION DISKS
NO ROOT FILE SYSTEM DEFINED



... what does that mean and how do i fix it? tHanks!! :)

---

### Post by JProgrammer on 2004-12-01
Well welcome to the world of Linux
 
 the root is where your filesystem starts
 
 so setup a partition on your hard drive with reiserfs
 
 and set the mount point to **/**
 
 you should proabbly format a swap partition to which is best at 2x the size of your ram. But if you have more than 512mb of ram try for the same amount

---

### Post by Infatuated_iPod on 2004-12-01
Sorry, what happened was that the mount was set to /home by default.. it was wierd. I fixed it.. Thanks anyway.

---

### Post by coastie on 2004-12-02
[QUOTE=JProgrammer]Well welcome to the world of Linux
 
 the root is where your filesystem starts
 
 so setup a partition on your hard drive with reiserfs
 
 and set the mount point to **/**
 
 you should proabbly format a swap partition to which is best at 2x the size of your ram. But if you have more than 512mb of ram try for the same amount[/QUOTE]
 i had this same problem. the file system of the partition i want isn't reiserf. does it need to be, for the install?

---

### Post by JProgrammer on 2004-12-02
No it doesn't need to be reiserfs it can be any of the availiable ones but you do need a mount point

---

### Post by coastie on 2004-12-03
ok a little background on my system. i am currently running suse 9.1 personal on my largest partition, hda6.
my swap is hda5, and i am trying to install ubuntu on hda7 which is approx. 3.5 gb.  i have a 900mhz pentium celeron and 196 MB ram. hda 7 did have vector on it with an ext3 file system. wouldn't my mount point be hda7, or do i need to delete it then recreate it with the ubuntu partitioner?

oh yeah my boot loader is grub.

---

