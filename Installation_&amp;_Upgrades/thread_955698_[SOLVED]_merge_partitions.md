---
title: "[SOLVED] merge partitions"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by rkakkar on 2008-10-22
I am running out of space on  my windows drive (ntfs). is there any utility (like partition magic for windows) where i can bit off a chunk from my ext3 partition and merge it with my windows partition?

---

### Post by prshah on 2008-10-22
> **rkakkar said:**
> I am running out of space on  my windows drive (ntfs). is there any utility (like partition magic for windows) where i can bit off a chunk from my ext3 partition and merge it with my windows partition?

System-Administration-Partition Editor; if you don't have that entry, [install gparted]("apt://gparted")

Things can get hairy if your ext3 is in an extended partition and you intend to add space to a primary partition; but it can be done.

---

### Post by logos34 on 2008-10-22
> **rkakkar said:**
>  where i can bit off a chunk from my ext3 partition and merge it with my windows partition?

only if the two partitions are contiguous.  You don't 'merge', but rather shrink the ext3 (using Gparted) and expand the ntfs into the free space.  If the ext3 partition in question is /, then you'll obviously have to work from Gparted on the ubuntu live cd.

---

### Post by rkakkar on 2008-10-23
> **prshah said:**
> System-Administration-Partition Editor; if you don't have that entry, [install gparted]("apt://gparted")

Things can get hairy if your ext3 is in an extended partition and you intend to add space to a primary partition; but it can be done.

unfortunately that's exactly what i want to do.

my partition table is as follows:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1095     8795556    7  HPFS/NTFS
/dev/sda2            1096       14593   108422685    5  Extended
/dev/sda5            1096       14219   105418498+  83  Linux
/dev/sda6           14220       14593     3004123+  82  Linux swap / Solaris

```

and now i want to take a chunk out of /dev/sda5 and merge it with /dev/sda1. how can i do so? gparted allows me to shrink /dev/sda5 but there is no option to merge the new space with /dev/sda1

---

### Post by logos34 on 2008-10-23
> **rkakkar said:**
> 
[/code]and now i want to take a chunk out of /dev/sda5 and merge it with /dev/sda1. how can i do so? gparted allows me to shrink /dev/sda5 but there is no option to merge the new space with /dev/sda1

Using Gparted on the live cd, shrink sda5 (from the left), then shrink sda2 to match.  Expand sda1 to incorporate the freed space.

good luck

---

### Post by rkakkar on 2008-10-23
> **logos34 said:**
> Using Gparted on the live cd, shrink sda5 (from the left), then shrink sda2 to match.  Expand sda1 to incorporate the freed space.

good luck

no luck. its not allowing me to shrink sda2 to match.

---

### Post by prshah on 2008-10-23
> **rkakkar said:**
> no luck. its not allowing me to shrink sda2 to match.

You need to "unmount" the swap; booting off a live CD activates swap if a swap partition exists.

From the live CD:

EITHER:

right click the linux-swap partition (in gparted) and choose "Swapoff"

OR:

Close gparted, open a terminal, and give the command```
sudo swapoff -a
```, then restart gparted

---

