---
title: "installation"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by rajesh.kanakabandi on 2010-04-25
hi geeks,
i've decided to install ubuntu from the cd. but i want to partition my disk into 5 partitions as..

1.root directory for the os
2.swap area
3.ext3
4.ext3
5.ext3

what mount points am i supposed to specify for the last 3 partitions?

i used to get these disks mounted in 
/media/disk1
/media/disk2
/media/disk3

do i have to mention it that way?

---

### Post by nitstorm on 2010-04-25
No need to mention any mount points. Just use "Do not use this partition"

---

### Post by rajesh.kanakabandi on 2010-04-25
> **nitstorm said:**
> No need to mention any mount points. Just use "Do not use this partition"

then will the partitions auto mount ?
i'm lazy to mount them manually every time i switch on

---

### Post by rajesh.kanakabandi on 2010-04-25
> **nitstorm said:**
> No need to mention any mount points. Just use "Do not use this partition"

linix is not even detecting the partitions... may be cause they are not formatted. now how can i format the partitions?

---

### Post by wmatthews on 2010-04-25
If you are finished with the install already just follow this tutorial to get your partitions to mount.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) 

Next time just do it while you are installing it would make everything much easier.

---

### Post by rajesh.kanakabandi on 2010-04-25
> **wmatthews said:**
> If you are finished with the install already just follow this tutorial to get your partitions to mount.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) 

Next time just do it while you are installing it would make everything much easier.

i have to reinstall. my problem with the partitions is to have separate partitions for different purposes.so decided to have them as 
[B]partition                                              mount point
[/B]1.root directory for the os(ext3)                          /
2.swap area
3.ext3                                                               ?
4.ext3                                                               ?
5.ext3                                                               ?

1.my hardisk has raw space so i need to format the partitions first. this is not being allowed when i choose the option do not use this patition.
2.when i choose ext3 and not select any mount point the installation is not proceeding.
3.when i give the mount point as /media/diskX it ends up with an error.
4.when i give /home for more than one partition it does not proceed.

i want all my partitions formatted and set to auto mount how can u help me?

thankyou.

---

