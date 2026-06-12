---
title: "internal, IDE HDD problem -chown-"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by Sharpiedeluxe on 2008-09-06
Ok, so basically, I just want to have this drive mounted with user permissions so that I dont need to be root to access it. Unfortunately, chown'ing the thing doesnt seem to work. In terminal, it says: "drwxr-xr-x  3 kurisu kurisu 4096 2008-09-06 18:41 sdb1", but in the GUI properties tab, it says that the permissions cannot be determined, and also that root owns the drive. 

fstab mounts it: UUID=1ad7d818-7b78-49fe-a350-bb5f4f4a42f0 /media/sdb1	  ext3	  relatime,errors=remount-ro 0	     1

I'm kind of at a loss..I've tried reformatting the drive and all. I can't seem to get this >.< If you need any other information let me know please.

---

