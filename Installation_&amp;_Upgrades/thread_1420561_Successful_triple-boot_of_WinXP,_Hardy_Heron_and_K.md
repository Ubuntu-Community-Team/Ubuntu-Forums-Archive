---
title: "Successful triple-boot of WinXP, Hardy Heron and Karmic Koala with Grub2 - How?"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by InspironDualBoot on 2010-03-03
I've read in many places that multi-boot is a problem. Maybe I'm just lucky - the following method seemed to work for me:

1) Use WinXP installation CD to partition disk, with a partition for WinXP, a partition for Karmic, and free space for Hardy.
2) Install WinXP. 
3) Boot Hardy Heron LiveCD and install into the free space.
4) Boot from WinXP installation CD again but only to convert the partition reserved for Karmic to free space.
5) Abort the Windows install and boot into Windows (Grub has disappeared and you can't boot into Hardy)
6) Boot from Karmic LiveCD and install Karmic into the  free space.
7) System now boots into Grub2 and allows me to select Karmic, WinXP or Hardy.

Q1) Has anybody else done something like this?

Q2) Can anybody explain WHY this seems to work?

---

### Post by oldfred on 2010-03-03
I always set my partitions up in advance but then I have been partitioning since CP/M days.

Yours is a good way since you did plan both the order of boot loader and planning ahead for the space needed for each install. Did you end up with two swaps or did the last install use the Hardy swap?

---

### Post by InspironDualBoot on 2010-03-04
Two swaps. The Karmic LiveCD created a new swap (in addition to the Karmic partition) within the space I'd freed up for installing it.

> Yours is a good way since you did plan...It may seem that way, but I did a lot of playing around before I got to this. (I was doing a complete reinstall of WinXP anyway, so it was a good opportunity)

Trial and error! ;)

---

