---
title: "bug in QTParted/Kubuntu installer"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Big_Croc7 on 2007-03-03
Hi, I've found a bug!

I've tried to install Kubuntu 6.10 and I've run into problems with the partitioner.  I'm running windows XP and want to dual boot; my hard disk is already partitioned (which I did with the GParted live CD), with a primary for XP and everything else in the extended.  When I get to the partitioner stage of the install something goes wrong - the numbers QTParted reports when reading partitions are DIFFERENT to when it writes to a partition;

example: I needed to format my desired root partition (reported as hda8, with the correct size, in QTParted).  Everything looks ok, until I commit the changes, only to find it's formatted hda6 instead!  I've tried both running the partitioner through the install program and running QTParted standalone - same result.

What do I do now? Is this a known problem (it seems serious!); if not, how do I report it officially?

---

