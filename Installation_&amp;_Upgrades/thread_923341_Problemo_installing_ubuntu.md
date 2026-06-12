---
title: "Problemo installing ubuntu"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by Colo2 on 2008-09-18
I:

Inserted disc
Followed the wizard
got to the part where it asked me about partitioning
I select resize and go for 50-50 (windows and ubuntu)
I click forward and it gives me an error message saying more or less: "cannot resize hda5" or something simluar, No error code or anything. I click OK and it directs me to another part of the partitioner. in this part there are 2 partitions listed. I choose hda5 and set the moint point to /, I choose journal Ex3 or something and click go, the formater launches up and gives me another cannot format drive error
can anyone help?

thank you :)

tom

---

### Post by Pumalite on 2008-09-18
Post:
sudo fdisk -lu

---

### Post by Colo2 on 2008-09-18
sudo: fdisc: command not found

---

### Post by SuperSonic4 on 2008-09-18
It's a k not a c

---

### Post by Colo2 on 2008-09-18
Im such an idiot, sorry

Disk /dev/sda: 122.9 GB, 122942324736
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 bytes
Disk indentifier 0xaf4a7372

   Device Boot      Start            end               blocks          ID      SYSTEM        
/dev/sda1  *           63           113740199          56870068+       7       HPFS/NTFS
/dev/sda2       113740200           240107489	       63183645        f       w95 Ext'd (LBA)
/dev/sda5       113740263	    240107489          63183613+       7       HPFS/NTFS

---

### Post by Pumalite on 2008-09-18
sda2 is an extended partition. That's why you cannot resize sda5. Delete sda2 with Gparted and then repartition your drive. Backup everything first.

---

