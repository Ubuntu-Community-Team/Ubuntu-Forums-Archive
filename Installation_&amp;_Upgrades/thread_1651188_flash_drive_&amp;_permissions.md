---
title: "flash drive &amp; permissions"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by bart11 on 2010-12-22
I installed Ubuntu 10.10 to a flash drive. I did not use the startup disk creator i did a normal installation.
    
    I created a fat 32 partition at the beginning of the flash drive so I would have some storage space when inserted on a windows box.
    
    everything seems to be working ok but I can not change permissions on the files located on the fat 32 partition. for example if I type &#8220;sudo nautilus&#8221; and then go to properties if i check the make executable option it will not stay ticked.
    
    can some one give me some ideas?

---

### Post by ottosykora on 2010-12-23
well nothing in a fat32 partition has any rights or any similar properties, there is simply nothing such there, so any rights will not be stored or changed etc.

---

### Post by bart11 on 2010-12-23
I think my problem lies in the mtab or fstab file.

here is the line in mtab.

/dev/sdb1 /media/2AE1-B021 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0

---

### Post by bart11 on 2010-12-23
I started playing around with pysdm and some how the executable property is set.

anyway my issue has been resolved and my bash scripts can be ran from the fat partition.

---

