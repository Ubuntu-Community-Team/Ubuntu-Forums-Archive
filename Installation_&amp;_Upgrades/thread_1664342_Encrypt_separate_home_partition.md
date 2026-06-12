---
title: "Encrypt separate /home partition"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by newboyo on 2011-01-10
Hi all,

This is a problem I've been trying to solve for a long time. I'd like to -
1. divide my HDD into separate partitions for Win7, /, ~ and swap.
2. install 10.4/10.10 such that ~ is encrypted.

While I can partition and install 10.4/10.10, encrypting the separate ~ has me foxed. 

Any suggestions for an intermediate newbie would be most appreciated. 

Rgds

New

---

### Post by Hegh on 2011-01-10
I don't know if the standard desktop install CD gives the option, but the alternate install CD asks you whether to encrypt your home directory as part of the installation.

It will basically create an encrypted filesystem image file which is then mounted as your home directory; upon login, it is mounted and your password is used to decrypt the key that keeps it safe. On logout, it is unmounted and becomes unaccessible without the key.

---

### Post by newboyo on 2011-01-10
Thanks for your reply. Would it allow for a separate ~ and /. My existing install clubbed ~ and / together in one partition, which is what I'd like to avoid.

---

### Post by Hegh on 2011-01-11
It will allow that, but you will need to manually partition your drive, as the auto-partitioner does not separate home from / for some reason.

When partitioning, I suggest a layout like this:

1G: /boot
2x RAM: swap
20G: /
Rest: /home

If you're feeling ambitious, and you're using the alternate installer, go with LVM. It  will allow you to easily (with the command line) shift space around between the partitions afterwards.

---

### Post by newboyo on 2011-01-11
Thanks very much indeed.

---

