---
title: "change of SHM/TMPFS mount points"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by smoczyna on 2012-08-08
Hi

After upgrade from 10.04 LTS to 12.04 LTS system changed the mount points of  tmpfs and shm from /dev to /run so I've got tmpfs mounted to /run and shm to /run/shm instead of /dev/shm. That fact makes few problem for me so I'd like go back to /dev instead of /run but I can't umount/remount it. Also my swap partitions is completely not in use, even not mounted after reboot although it is on the list in fstab file, I have to manually call swapon every time. 

How can I fix those issues? I can't start my oracle database complaining for lack of shm mounted.

---

