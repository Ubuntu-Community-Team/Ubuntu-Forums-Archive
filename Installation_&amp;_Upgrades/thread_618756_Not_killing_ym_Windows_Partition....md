---
title: "Not killing ym Windows Partition..."
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by wydra on 2007-11-20
Ok really quickly, let me know if I got this striaght.

Basically, what is know as my windows partition is the C:\ Drive in windows? Right?

When I create a partition to install Ubuntu on, it creates a barrier windows cannot cross into, that Ubuntu uses only for itself. Right? Or can windows browse in it? Like a D: drive?

Here's my dillema. The other day, I installed Ubuntu, when I set it to make a partition for itself, it managed to corrupt my windows partition.

Currently, since I COMPLETELY wipe my comp and re installed windows, is it possible for me to "divide" the windows partition, and install ubuntu on that without corrupting my partition again? BTW, I do have cute partition manager.

---

### Post by taurus on 2007-11-20
Partition:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Install:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Access Ubuntu partition while in windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by wydra on 2007-11-20
So basically, after I backup my files, I could just use the first option for my HD, and give windows mor room than linux? 

(I only plan to use Linux for Blender and GIMP)

---

### Post by taurus on 2007-11-20
The easiest way to go is to divide your harddrive into two partitions.  Install windows on the first partition and then install Ubuntu on the second partition.  Ubuntu installer knows what to do with that second partition, dividing it into two  partitions:  one for / and one for swap.

---

### Post by wydra on 2007-11-21
What if windows is already installed? Just split the existing partition and install on the second one?

---

### Post by Sef on 2007-11-21
> What if windows is already installed? Just split the existing partition and install on the second one?

That is correct.  You should have an XP partition, a Ubuntu partition, a home partition that is shared or a home and a shared partition, and swap, if you have less than 1 gb ram.  Read up on how to set it up in the links provided above.

---

