---
title: "partioning gone wrong"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by robert fallis on 2007-05-12
I've just installed Ubuntu 6.06, I intended to keep my Suse partion but did not get the partioning quiet right, so what I'm left with is ubuntu,. and a large partion (hda3) which I cannot access, ( it belongs to root) is there any way to change the permissions on this disk so that I can access it for storage

bob

---

### Post by uantuzri on 2007-05-12
I'm not quite sure, but maybe Disk Manager can help you.
 [http://flomertens.free.fr/disk-manager/index.html](http://flomertens.free.fr/disk-manager/index.html) 
There's a deb for ubuntu.

---

### Post by henkth on 2007-05-12
Hi, open a terminal from Applications - Terminal.
Then type:

sudo chown -R username /mount_location/

(fill in your username and name of the partition)

Now you can use that partition to Read/Write on the new partition.

Henk.

---

