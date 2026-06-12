---
title: "Ubuntu 9.10 No operating systems Dell E6500"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by spigy11 on 2010-03-11
Hi guys

I just want to install Ubuntu 9.10 x86 on my company laptop, but Im getting confused.

When loading LiveCD eveything works normal, every piece of hardware is detected nice ;)

But.... when I try to install I get the message by partitions no partitions found, and no operating systems found either.

when executing fdisk -l I get
/dev/sda1 dell utility - ?? wth?
/dev/sda2 NTFS
/dev/sda3 NTFS

When I click customize partitions it shows me only the /dev/sda drive without any existing partitions, but they are there!!!


I tried already Wubi, and its working, but want to install ubuntu reall.

I will welcome any tips or suggestions which could help to solve my problems.

txs you in advance

---

### Post by jjcv on 2010-03-11
> **spigy11 said:**
> Hi guys

when executing fdisk -l I get
/dev/sda1 dell utility - ?? wth?
/dev/sda2 NTFS
/dev/sda3 NTFS



Is this Drive C:\ (sda2) and Drive D:\ (sda3) in your Windows install?

If so can you move everything off D:\ into c:\ and then use fdisk to remove /dev/sda3 so it has space to install Ubuntu?

I am guessing you have no free space to install.

Make sure you have a backup.

---

### Post by spigy11 on 2010-03-12
Hi

as mentioned gparted, opensuse, ubuntu nor fedora installer was unable to recognize from installation wizard what partitions are present.

Still I have done it my way :D

1. I wiped the whole HDD
2. installed Ubuntu, came to work, activated 802.11x authentication, installed Evolution mapi-exchange, mounted by shares my samba, and go to toilet to s...t on windows :D

I have lost my data, but I have mostly all on my externall hdd and flashstick

---

