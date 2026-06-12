---
title: "two ubuntu and a window installed"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by vishankita on 2011-02-08
hey
I have  got ubuntu installed two times on my system plus windows xp which crashed before. Problems are following-:
1) i can't figure out how to retrieve files/data i had on my system before windows crashed without reinstalling windows ?
2) how can i un-install/remove other two operating systems( windows and previously installed ubuntu) ?

i installed ubuntu both the times using burned cd after downloading it from internet. i am new user of ubuntu. computer shows: 160GB hard disk 45 GB Filesytem , 160 GB hard disk 71 GB Filesystem , 160 GB  hard disk presario_rp.. . While installing latest ubuntu i divided 160GB hard disk into 45GB and 115 GB which esplains the first part. what are the other two.

---

### Post by oldfred on 2011-02-08
Wecome to the forum.

Post this to see all partitions.

```
sudo fdisk -lu
```

The presario is probably a recovery partition. Vendors stopped giving install disks and just created a image file of the hard drive as it was when you purchased it. It usually is one of the 4 primary partitions that you can have. If you installed Ubuntu into an extended partitions that may be what the rest is?

---

