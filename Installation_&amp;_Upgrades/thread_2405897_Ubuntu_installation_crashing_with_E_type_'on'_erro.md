---
title: "Ubuntu installation crashing with E: type 'on' error"
date: 2018-11-12
forum: Installation &amp; Upgrades
---

### Post by qushaes on 2018-11-12
Hello, I tried to run windows recovery but it crashed. I had installed Ubuntu on my secondary drive but had formatted the disk from within windows. Now when I try the Ubuntu installer it gives me the error "E:type 'on' " when trying to create an ext4 partition. Is it an MBR problem, do I have to get a new hard drive? Any help would be appreciated, thanx.

---

### Post by ajgreeny on 2018-11-13
I think partitions created in Windows are dynamic and can not be seen properly nor used by Linux of any sort.

I am not sure how best to remove those partitions and create new ones using a live Ubuntu as I don't know if gparted will see them, but I presume you will be able to delete the partitions using Windows and leave unallocated space which Linux will see.

---

