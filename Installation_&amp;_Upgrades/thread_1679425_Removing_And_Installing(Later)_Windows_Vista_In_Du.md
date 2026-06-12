---
title: "Removing And Installing(Later) Windows Vista In Dual Boot"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by Hitman.sunny on 2011-02-01
I have installed vista(Preloaded) and Ubuntu 10.10 in dual boot in my laptop.
Now i want to get rid of vista, and want to have only Ubuntu, also i want to assign all space to Ubuntu.
I have two query's 

1. How could i cleanly uninstall  Vista from my system? (I Used WUBI to install Ubuntu)
2. Can i install Vista in future? (As my Vista was preloaded, Vista didn't recognize the hard drive on which Ubuntu is installed)

---

### Post by Mark Phelps on 2011-02-01
> **Hitman.sunny said:**
> I have installed vista(Preloaded) and Ubuntu 10.10 in dual boot in my laptop.
Now i want to get rid of vista, and want to have only Ubuntu, also i want to assign all space to Ubuntu.
I have two query's 

1. How could i cleanly uninstall  Vista from my system? (I Used WUBI to install Ubuntu)

Answer ... not easily ... as a Wubi install embeds Ubuntu INSIDE MS Windows, such that if you remove Windows, you erase Ubuntu in the process.

> 2. Can i install Vista in future? (As my Vista was preloaded, Vista didn't recognize the hard drive on which Ubuntu is installed)
IF you have a Vista install DVD (and a legit product key) you can install Vista any time you want -- but since you mentioned "preloaded", I'm guessing you have NO disk. Right?

On preloaded systems, vendors typically save a compressed OS image in a partition (sometimes hidden) on the hard drive.  If you still have that partition, and a way to invoke Vista restore (usually through a function key, or using a CD that came with the machine), you will be able to reinstall Vista later -- back to the original state it was in when you first used the machine.

If you erased that partition, you will NOT be able to reinstall Vista.

---

### Post by Hitman.sunny on 2011-02-01
Thanks Mark,
You are right i did the same i.e. assigning all space to ubuntu except recovery partition.
As i was formatting my system so was not able to access net, i had to format my HD for 3 times to understand the consequences.

---

