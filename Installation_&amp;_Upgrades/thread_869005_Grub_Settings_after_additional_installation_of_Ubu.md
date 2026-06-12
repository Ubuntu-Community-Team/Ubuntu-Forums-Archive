---
title: "Grub Settings after additional installation of Ubuntu 64Bit"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Euphorion on 2008-07-24
Hallo

I plan to install Ubuntu 64 in addition to my Ubuntu 32 Bit in order to perform a soft migration. As I also have Vista installed and Boot using EasyBCD the question that I am facing is how will repartitioning affect Grub and my current beautifully setup Ubuntu 32 Bit.

Currently I have the following Setup on a Fujitsu XI-2550 Laptop.

The first Harddisk contains the Vista recovery partition and Vista.
The second Harddisk contains 3 Partitions:
The first partition contains a common Data Area
The second partition contains Ubuntu 32 Bit
The third partition contains Ubuntu swap
Grub is in Harddisk 2 Partition 2 (hd1,1) (required by EasyBCD

I now want to insert a new partition between the common Data Area and Ubuntu 32 in which to install Ubuntu 64 Bit.

I can imagine that this will move Ubuntu 32 Bit to Partition 3 along with Grub (hd1,2), my current Menu.lst references hd1,1 .

When installing Ubuntu 64 I will instruct the installer to use Partition 2 and share the swap with Ubuntu 32 Bit and will Install grub in the new Partition 2 (hd1,1).

My Questions are the following:

1. is this feasible ?
2. How do I tell Ubuntu during install to share the Swap, use existing swap partition
3. Will I have to edit Grub in order to boot the 32 bit version and if yes what must I edit and what must I modify. I assume menu.lst and change hd1,1 to hd1,2
4. Will the 2 Grubs collide

Naturally I will have to reconfigure EasyBCD.

When modifying the Partition data I will use Gparted from a boot CD. I would like to avoid the other alternative that springs to mind and that would be to move the 32 Bit Partition forward so that it remains partition 2 (hd1,1) but then how will the 32 bit version know that its swap partition is partion 4 and once again will Grub be affected as all relevent boot data has physically moved. To safeguard against calimity I have saved everything to an external Hard Disk using Acronis True Image.

Would greatly appreciate your help and advise on this matter, thanks in advance

---

### Post by logos34 on 2008-07-25
It looks like the new partition created for x64 ubuntu will be sdb4 (partitions are numbered in the order they are created, not disk order).  It will detect and use the existing swap.  Let it install grub--it should detect the other OS's and on reboot you will have a choice on the grub menu screen. 

Edit EasyBCD linux entry to point to x64 /

---

### Post by Euphorion on 2008-07-25
Thank you very much for your advise, I was not aware that Partitions are numbered according to order of creation. This fact makes installing the 64 Bit Version a lot easier.

---

