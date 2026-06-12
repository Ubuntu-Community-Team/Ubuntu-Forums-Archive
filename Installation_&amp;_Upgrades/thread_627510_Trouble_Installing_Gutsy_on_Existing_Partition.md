---
title: "Trouble Installing Gutsy on Existing Partition"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by carlos_ on 2007-11-30
I want to do a clean install of Gutsy over an existing partition.  However, when I get to the part where where I choose partitioning, I'm not presented with a choice of existing partitions.  More specifically, I'm given two options: 1. "Guided - use entire disk" or 2. "Manual.  Since I don't want to use the entire disk, I select option #2.

When I select "Manual", all I see is "/dev/sda" referring to the main drive. I thought I would be able to see a list of my partitions.  However, I can then only select "New partition table" or "Undo changes to partitions".  If I select "New partition table" I get a message telling me  that I have selected an entire device to partition... I don't want this, I only want to use a subset of the drive, i.e. an existing partition.

Am I missing something?

---

### Post by Pumalite on 2007-11-30
Get Gparted Live CD and see if it sees your partitions. If it does, reformat your chosen partition ext3

---

