---
title: "How to increase the size of the root disk?"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by studentpower on 2007-10-04
when I type > df, it lists my disk usage like below:
Filesystem    1K-block       used       Available       Use%    Mounted on
/dev/sda3     2103072    2081808             0         100%       /


How could I increase this size to release some room from /dev/sda1 where stores my user files?

---

### Post by Pumalite on 2007-10-04
An installation of Ubuntu needs:
Minimum 10 GB for '/'
500 MB for /swap
The rest for /home
Post:
sudo fdisk -lu
df -h

---

### Post by studentpower on 2007-10-04
Thanks. Have to reinstall.

---

### Post by Pumalite on 2007-10-04
You are welcome. Good luck.

---

### Post by jastonas on 2008-05-03
Re-Install only solution?????

---

