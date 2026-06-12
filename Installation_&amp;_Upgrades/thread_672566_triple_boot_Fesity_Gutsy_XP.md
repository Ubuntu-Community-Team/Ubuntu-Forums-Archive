---
title: "triple boot Fesity Gutsy XP"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by ewy on 2008-01-19
I currently have a fresh copy of WinXP running, using the full 60GB of my HDD. I'd like to install both 7.04 and 7.10 to run on this computer, but I haven't been able to find a good guide to proceed with. Can anyone recommend a How-To, a guide, or a resource for tips?

Cheers.

---

### Post by WearZeeP on 2008-01-19
Well I if you already have windows installed I would just use the Ubuntu LiveCD (i think there is gparted on it), and shrink your windows partition, then make two new ones, and then install feisty on one, and gutsy on the last one.
That should work.

---

### Post by ewy on 2008-01-20
Fair enough -- my apologies, I didn't state at the outset what I had hoped for. I would like the following partitions:

WinXP
FAT32 shared (/home)
Ubuntu 7.04
Ubuntu 7.10
Ubuntu SWAP

I have heard it is also a good idea to create a separate partition for GRUB. Either way, the total number exceeds 4, so I'd have to wrangle some sort of extended partition setup, and I'm not sure how all that works. Worst case I could eliminate the GRUB and shared FAT32 drive and squeak by with 4 primary partitions, but in terms of troubleshooting or later installs that means my data is a little more constricted.

---

