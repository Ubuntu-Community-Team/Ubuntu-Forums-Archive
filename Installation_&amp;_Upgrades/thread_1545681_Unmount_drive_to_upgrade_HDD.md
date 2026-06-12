---
title: "Unmount drive to upgrade HDD?"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Blueblib on 2010-08-04
I have a 160GB drive installed as /dev/sdb. If I replace it with a 500GB drive, do I have to unmount/mount or will it work as is? This is on Ubuntu Server.

---

### Post by ajgreeny on 2010-08-04
If it is mounted at the moment by /etc/fstab at boot time, you will probably need to edit fstab to take account of a new UUID for that disk/partition.  Apart from that there should be no problems.

---

