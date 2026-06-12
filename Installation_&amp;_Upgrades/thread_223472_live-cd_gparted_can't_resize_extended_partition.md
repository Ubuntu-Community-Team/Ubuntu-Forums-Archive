---
title: "live-cd gparted: can't resize extended partition"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by ghee22 on 2006-07-26
I have my root & home partition inside an extended partition.  I have resized my home partition from 50 to 20 gigs, leaving me with 30 gigs of unformatted space in the extended partition.

How do I resize the extended partition to move the 30 gigs of unformatted space outside of the extended partition?  Gparted won't let me resize the extended partition!

---

### Post by Mike_N on 2006-07-26
1: Are you using the current version of the G-Parted boot disk?
2: What happens when you try?

---

### Post by ghee22 on 2006-07-26
> **Mike_N said:**
> 1: Are you using the current version of the G-Parted boot disk?
2: What happens when you try?
1. I am using the latest Ubuntu Dapper Drake Live-cd 6.06.
2. When i select the extended partition, the only link in the context menu enabled is Information

---

### Post by mod187 on 2006-07-26
I had trouble resizing a partition that had XP installed on it with the latest gparted live CD. When I selected the drive, I clicked on 'Manage Flags', and removed the checks in the boxes for the flags, and it let me change the sizes then. I don't know if I had to restart gparted again before I could resize, or if it was instant, but it worked for me.

After making the changes, I had to boot to gparted again and return the flags that I removed before it worked.

Hope this may help

.\\

---

