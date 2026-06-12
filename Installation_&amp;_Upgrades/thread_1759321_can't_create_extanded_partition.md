---
title: "can't create extanded partition"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by sam1948 on 2011-05-15
image attached from gparted on ubuntu 11.04
any idea?

---

### Post by Quackers on 2011-05-15
You already have an extended partition. There can be only one extended partition on a disc. Because the unallocated space is next to your extended partition you can extend your extended partition into that unallocated space. Then you can create more logical partitions or extend sda6.
You cannot do this while the file system is mounted. You should do it from a live cd/usb desktop or by using a gparted live cd.

---

### Post by lechien73 on 2011-05-15
I think you're best running gparted from a Live CD, because you will need to unmount the extended partition.

Also, you can only have one extended partition per drive, so I think what you mean is that you want to create another logical partition inside the extended one.

To create a new logical partition, right click on the unmounted /dev/sda2 and click New.

---

### Post by lechien73 on 2011-05-15
I must be slowing down in my typing...that's the 2nd time I've duplicated an answer today :)

---

### Post by Hedgehog1 on 2011-05-15
> **lechien73 said:**
> I must be slowing down in my typing...that's the 2nd time I've duplicated an answer today :)

It is not that you are slow - it is that **Quackers** is really fast!


***The Hedge***

:KS

---

### Post by sam1948 on 2011-05-19
thanks people (:
no more than one extended was what i needed.

---

### Post by Quackers on 2011-05-19
Glad to see you got things sorted out :-)

Mr Hedge, you should get some webbed feet! You can type like a maniac with these things :-)

---

