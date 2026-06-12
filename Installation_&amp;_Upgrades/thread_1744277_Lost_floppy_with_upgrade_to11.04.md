---
title: "Lost floppy with upgrade to11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Krister Hallergard on 2011-04-30
Cannot mount floppy after upgrading from 10.10 to 11.04, with same entry in fstab.  Have tried changing auto in fstab to ext2,3xt3,vfat,msdos but problem remains.  Help would be appreciated.
Cheers, Krister

---

### Post by Krister Hallergard on 2011-05-02
Found the solution:  Change in /etc/fstab from  /etc/fd0  to /etc/fd0u1440

---

