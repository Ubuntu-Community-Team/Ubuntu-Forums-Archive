---
title: "Installing a new distro with a separated boot partition"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by ShacaL on 2011-11-13
Hello :)

I have a notebook installed with Kubuntu. I'vve separated my partitions with this configuration:

swap 2GB
home 200GB
root 20GB
boot 500MB
free 15GB

I did with a separeted boot partition, I don't remember why. But now I want to install Chakra in the free space, and I don't know if I have to set the current boot partition as the boot partition of the new distro, or I just install Chakra in the free space and don't touch the other partitions. (just the home partition, cause I need some space for my files)

Sorry if I wasn't enough clear, my english sucks.

---

### Post by darkod on 2011-11-14
You can use just the free space. You don't have to use the /boot partition from Kubuntu for the new install. I think it might be even better to keep the boot files separate. Without a separate /boot for Chakra the boot files will be on the / partition.

---

