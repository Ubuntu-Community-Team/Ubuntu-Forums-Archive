---
title: "Editing fstab..."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by snakedog on 2008-05-01
I installed Xubuntu 8.04 without adding mount points for 
the two FAT32 partitions on this HDD.  

Rather than reinstall, I figured to edit fstab.  

Do I need to edit mtab, too?

I've got Xubuntu 6.06 on an old Compaq laptop, and it is 
similarly partitioned.  Can I more or less copy the lines 
I need to mount the partitions on the 8.04 machine from 
the 6.06 machine to fstab?  

I am somewhat familiar with fstab and know to make a backup 
copy.  Just want to make sure nothing's radically changed
in 8.04 and I have what I need to go forward.

Thanks.

---

### Post by njparton on 2008-05-01
Just fstab then:
 
```
sudo mount -a
```

---

