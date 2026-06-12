---
title: "How to install edgy from liveCD with debootstrap without network?"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by jihocech on 2006-11-04
Hello,
 I would like to install edgy on my new computer with SATA fakeRaid. But, I don't know how to do it without network access.
I have only liveCD and debootstrap and dmraid. After booting live cd, I install dmraid and prepare partitions, then I try to use installed debootstrap, but i got errors. There is my way:

1) Boot live cd
2) sudo -s root
3) Install dmraid and prepare partitions
4) SwapOn
6) Create mountpoint mkdir /target
6) mount partitition mount -t ext3 /dev/mapper/raid1 /target
7) install debootstrap
8] use debootstrap "debootstrap edgy /target file:/cdrom"

- after last command I receive Warning: "Failure trying to run: chroot /target mount -t proc proc /proc"

I don't know, how to solve this problem. Is there anybody who know the way, how to solve it, please ?

---

