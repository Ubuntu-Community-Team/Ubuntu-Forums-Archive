---
title: "file system"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by muggins on 2006-10-12
Trying to install edgy eft. Which file system should I select when making new partition for ubuntu?

---

### Post by JonahRowley on 2006-10-12
The installer should make the filesytem for you.  How are you trying to create a filesystem?

---

### Post by wpshooter on 2006-10-12
> **muggins said:**
> Trying to install edgy eft. Which file system should I select when making new partition for ubuntu?

My suggestion would be to make "/" ext3, make "/home" ext3, and make "swap" swap.

Good luck.

---

### Post by muggins on 2006-10-12
> **wpshooter said:**
> My suggestion would be to make "/" ext3, make "/home" ext3, and make "swap" swap.

Good luck.

Thanks for replying. Do I need a third partition "/home"?

---

### Post by muggins on 2006-10-12
> **JonahRowley said:**
> The installer should make the filesytem for you.  How are you trying to create a filesystem?

I am dual booting with xp and manually setting partitions with gparted.

---

### Post by taurus on 2006-10-12
You don't need a seperate /home if you don't want.  However, if you decide to re-install it again, then all your personal stuff in /home will be saved, assuming you don't tell the installer to reformat /home again...  So basically, you need at least two partitions if you plan to install Ubuntu:  / & swap.

---

### Post by muggins on 2006-10-14
Thanks everybody for your help. I have edgy downloaded now with just the two partitions. Have noticed so far that edgy is a lot faster than dapper was. Don't know if I messed something up with dapper or if edgy is just plain faster.

---

