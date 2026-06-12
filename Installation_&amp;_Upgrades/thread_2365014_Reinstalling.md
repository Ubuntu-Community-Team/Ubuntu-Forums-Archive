---
title: "Reinstalling"
date: 2017-07-01
forum: Installation &amp; Upgrades
---

### Post by wfp on 2017-07-01
Amuse me please. Just wondering if this should work. Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1936828415 1936826368 923.6G 83 Linux
/dev/sda2       1936830462 1953523711   16693250     8G  5 Extended
/dev/sda5       1936830464 1953523711   16693248     8G 82 Linux swap / Solaris


I want to reinstall windows, and instead of  getting rid of grub, and fixing mbr. Could I just not open gparted, and umount /dev/sda1 , and then delete partition, then convert free space to ntfs, and throw in windows installation cd.

---

### Post by ubfan1 on 2017-07-01
Windows would not need the extended or swap partitions, so that space is wasted,  and when you remove sda1, grub looses all its files, so no.

---

### Post by deadflowr on 2017-07-01
Indeed, if you want to remove Ubuntu/linux from the sda1 partition, then you'd be better off simply clearing the whole disk, and leave it as unallocated.
Windows will see the disk as empty and set up the partitioning it needs properly.

(If you wanted to just resize Ubuntu/linux and leave space for Windows, then that would be a whole nother thing.)

---

### Post by ubfan1 on 2017-07-01
You could try lubuntu on that machine if performance of Ubuntu is a problem.

---

### Post by wfp on 2017-07-02
Thanks for all your input.

---

