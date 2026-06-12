---
title: "Edgy wont partition properly"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by pgmer6809 on 2007-04-02
Hi I have a current system, with two drives. hda=10GB, hda1=swap, hda2=ext3
hdb1=78gb fat32, hdb2=ext3.
hda2 currently has Mepis installed, hdb has a bunch of data I want to keep.
Running edgy installer, I ask for manual partition.
it sets up to make hdb2 the root (/) partiotion, , and wants to mount the others on /media
It says it is going to reformat /hdb2.
Of course I change this. I tell it to use the swap partition on hda1, and the root (/) partition on hda2, and not to mount the hdb drive at all. 
I check the reformat boxes on the two hda partitions.
But edgy comes back and says there is no root partition  and refuses to go further.

The disk is OK because when I exit edgy I can boot Mepis fine.

What can I do to prevent edgy from formating all my data?

pgmer6809

---

