---
title: "Help in partitioning Vista for installing 8.10"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by F8M on 2008-11-25
I have tried partioning in two different ways in Vista, but none seem to work when installing the Ubuntu 8.10 live CD. I first shrinked Vista to leave 15,000 for Ubuntu as a swap file. And when that did not work, I shrinked Vista to leave 15,000 for Ubuntu as an empty file(unallocated). Can you please help me as to how to partition Vista so I can install Ubuntu 8.10 frome the live CD - THANK YOU.

---

### Post by taurus on 2008-11-25
Maybe these help.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)

---

### Post by DLF44 on 2008-12-05
if i choose the "guided - use entire disk" partition, is that permanent? and also does it wipe out all of my files from windows? or is there a way to transfer them into ubuntu?

---

### Post by generic_idea_machine on 2008-12-05
> **DLF44 said:**
> if i choose the "guided - use entire disk" partition, is that permanent? and also does it wipe out all of my files from windows? or is there a way to transfer them into ubuntu?

that option does exactly what it says. So your files are gone. Sorry dude

---

### Post by DLF44 on 2008-12-05
thanx for the quick reply.

if i choose to make a windows / ubuntu partition, can i get rid of the windows one at a later time?

id justlike to try and get my files into ubuntu

---

### Post by Mark Phelps on 2008-12-05
First off, please start the LiveCD and post the results of "fdisk -lu" (that's a small ell, not a one).  That will tell us what partitions exist on your machine.

Second, you were right in NOT choosing the option presented as that would have reformatted your drive and wiped Vista.  The option to use is the one that references free space.  Another reason we need to see the fdisk results.

Third, if automatic partitioning doesn't work, you can always use the alternate CD and do manual partitioning.

---

### Post by razy60 on 2008-12-05
If you only have the one partition, when it gets to guided there is usually a yellow box to the left of the main box, that will say 8.10 in it. If you click on the yellow portion you can normally drag it to the right which will extend the windows partition.

Raz

---

