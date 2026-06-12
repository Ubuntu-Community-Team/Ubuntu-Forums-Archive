---
title: "I have a small problem with writting to fat32 premission"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by beko on 2006-06-12
Hi.. 
I have already mounted my 2 partitions ( fat32 )but I can't write to them & i think it's premission problem or maybe they way i put the mount point inside fstab. 
I tried to add my mount points like this :

/dev/sda1            /media/C           vfat       users,gid=users,umask=0002,utf8=true 0 0
/dev/sda5            /media/D           vfat       users,gid=users,umask=0002,utf8=true 0 0

Is there anything I need to do to be able to write to these partitions ? Sometimes I try to save any picture while browsing with firefox but it always give me error that it can't write to this partition.

---

### Post by aysiu on 2006-06-12
Try this instead: ```
/dev/sda1 /media/C vfat iocharset=utf8,umask=000 0 0
/dev/sda5 /media/D vfat iocharset=utf8,umask=000 0 0
``` Don't forget to do ```
sudo umount /dev/sda1
sudo umount /dev/sda5
sudo mount -a
``` after you change your /etc/fstab

---

### Post by beko on 2006-06-12
Worked Perfect

Thank you so much:lol::lol::lol::lol:

---

