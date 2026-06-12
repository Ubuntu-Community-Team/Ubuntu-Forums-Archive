---
title: "trouble partitioning"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by maxi123 on 2007-08-02
i have a gateway laptop and im tryin to partition my HD so that i can run windows and ubuntu...

i got all the way to the partitioning i cant shrink my windows partition using Gparted.. it gives me an error when i apply the pending operations... i think it might have to do with an unallocated space of 7.84MB which is the free space following (Mib) from the windows partition

also theres a system recovery partition..

this is how my hard drive looks

/dev/hda2    fat32    size :4.34GiB  used 1.97 GiB
/dev/hda1    ntfs      size : 88.81GiB used 24.05 GiB  Boot
unallocated   unallocated   7.84 MiB      

im hoping to shrink my windows partition to 50 GiB

thanks for your help 

NOTE: i tried doin the guided installation but i only get the option to use my entire hard drive and the option that says use biggest free space gives me an error sayin that the space might be to small

---

### Post by Pumalite on 2007-08-02
XP or Vista?. It makes a difference.

---

### Post by maxi123 on 2007-08-02
XP Media edition

---

### Post by Pumalite on 2007-08-03
Defrag several times, erase all temp files, then use Gparted: ( the stand-alone-burn-to-a-CD program): [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to shrink your XP partition. I would get rid of the rescue partition and get an OEM XP CD for 10 bucks. You can use the serial # in your laptop.

---

