---
title: "Ubuntu replace windows/ubuntu boot"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by jakegrant41 on 2012-02-27
Hi, i would like to remove my current windows and ubuntu dual boot and do a fresh install but i cant format the HDD from within windows nor ubuntu as i can remember the ubuntu password and the windows error message is Windows cannot format this partion.
 
Would it work if i ran the ubuntu installer and chose to overwrite my vista partion or would that mess up the hard drive?

---

### Post by ajgreeny on 2012-02-27
> **jakegrant41 said:**
> Hi, i would like to remove my current windows and ubuntu dual boot and do a fresh install but i cant format the HDD from within windows nor ubuntu as i can remember the ubuntu password and the windows error message is Windows cannot format this partion.
 
Would it work if i ran the ubuntu installer and chose to overwrite my vista partion or would that mess up the hard drive?
Running the ubuntu installer and choosing to use the whole drive would work without problems.

But if you have a good installation of ubuntu already running well, why bother to re-install?  You can use gparted from a live ubuntu CD to delete the windows partition(s) and then make a new partition in the space freed.  This can easily be mounted at boot time with a simple edit of **/etc/fstab** and you can use that new partition as a storage or data partition.

Come back again if you need more help.

---

### Post by jakegrant41 on 2012-02-28
> **ajgreeny said:**
> Running the ubuntu installer and choosing to use the whole drive would work without problems.
 
But if you have a good installation of ubuntu already running well, why bother to re-install? You can use gparted from a live ubuntu CD to delete the windows partition(s) and then make a new partition in the space freed. This can easily be mounted at boot time with a simple edit of **/etc/fstab** and you can use that new partition as a storage or data partition.
 
Come back again if you need more help.
I would rather start the HDD from a fresh OS, so would running the ubuntu installer from the USB then choosing to replace windows format the HDD and allow me to directly boot into the new ubuntu install?

---

### Post by ajgreeny on 2012-02-28
> **jakegrant41 said:**
> I would rather start the HDD from a fresh OS, so would running the ubuntu installer from the USB then choosing to replace windows format the HDD and allow me to directly boot into the new ubuntu install?
Yes, it would.

Have you considered having a separate /home partition?  It makes life a lot easier next time you need to install the OS from scratch.  Highly recommended!
See [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") for details.

---

