---
title: "Can't create swap space - 'unusable' - PLEASE HELP!"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by Perpetual_Bliss on 2011-03-15
I'm trying to install Ubuntu 10.10 netbook edition on my ASUS netbook (eee pc 1001p). My computer already came with 4 partitions - C, D (empty), recovery, and efs. I tried to install Ubuntu on my empty D drive, but it tells me that I need to create swap space to install. 
 
But when I go back and try to create a logical partition on my D drive so I can use that for swap space, it doesn't give me that option.
 
I've also tried reducing the size of my D drive to leave some empty space, but it just calls it 'unusable" and won't let me create a logical drive there either - PLEASE HELP!
 
What do I do? How do I complete my installation??
 
I really need to get this installed tonight because I have to use my comptuer soon! Thanks!

---

### Post by coffeecat on 2011-03-15
It's because you have four primary partitions, which is the maximum number allowed in an mbr partition table, which is what you have. To create more than four partitions you need to replace one primary with an extended partition. An extended partition is a special type of primary whose sole purpose is to act as a placeholder for a number of logical partitions. If your "D: drive" (please note this is a Windows convention which has no meaning in Linux) is large enough for both a Linux root partition and swap partition, then delete the so-called D: partition, create an extended partition in that space and then you will be able to create your Linux logical partitions in the extended partition.

Fortunately, Linux can boot from a logical partition which Windows cannot.

**EDIT**: if you need help with that, boot into the live USB session, open Gparted and post a screenshot of the Gparted window.

---

### Post by Perpetual_Bliss on 2011-03-15
> **coffeecat said:**
> It's because you have four primary partitions, which is the maximum number allowed in an mbr partition table, which is what you have. To create more than four partitions you need to replace one primary with an extended partition. An extended partition is a special type of primary whose sole purpose is to act as a placeholder for a number of logical partitions. If your "D: drive" (please note this is a Windows convention which has no meaning in Linux) is large enough for both a Linux root partition and swap partition, then delete the so-called D: partition, create an extended partition in that space and then you will be able to create your Linux logical partitions in the extended partition.

Fortunately, Linux can boot from a logical partition which Windows cannot.

**EDIT**: if you need help with that, boot into the live USB session, open Gparted and post a screenshot of the Gparted window.
Thanks so much! I deleted the D drive and extended the C drive. When I went back to Ubuntu installation, it had an option to install "side by side", which let me create a new partition for Ubuntu and installed seamlessly - LOVE IT! :) Thanks<3

---

