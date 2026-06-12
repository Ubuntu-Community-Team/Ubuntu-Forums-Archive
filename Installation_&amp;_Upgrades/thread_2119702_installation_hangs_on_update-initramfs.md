---
title: "installation hangs on update-initramfs"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by maharris on 2013-02-24
When install it hangs on not only the second screen when you select to download additional updates, but if i ever get past that. (i have to change initramfs.conf to dep and only then will it move past that) 

 then it hangs on

update-initramfs generating 3.5.0-17-generic

help!

thank you!

---

### Post by TheFu on 2013-02-24
Verify that all partitions are not out of space.
$ df -kh
$ df -i

---

### Post by maharris on 2013-02-24
i deleted the partition and hopefully it will work

---

### Post by maharris on 2013-02-24
it worked! after deleting the partition and using a non-corrupted disk image it works!

---

### Post by banifou on 2013-05-03
Please explain how? I have the same problem. i've never had to remove a partition yet. thanks

---

