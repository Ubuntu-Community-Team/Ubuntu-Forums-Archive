---
title: "[SOLVED] Working disk yet not mounted"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-12-06
Please start by seeing the attached screenshot. All the partitions report as being "unmounted".  I have 2 hard drives. One is/was bare metal. In an install scheme a little backwards from the usual, I have a 20gig as pri/slave and a 320gig as pri/msr. The bare metal is the 320gig. 

Using Ghost4Linux, I cloned the 20 gig to the 320 gig. Reset the bios to use the 1st hard drive (pri/mstr) as the "boot" drive and Low! and Behold, the 320 gig acts fine. Well almost. The partitions from 20 gig were on the 320 gig. So, using GParted LiveCD, I moved the partitions around. Only problem, the partitions aren't mounted. Nuts!

What needs doing to mount the drive? Modify fstab?

a little help, please.

---

### Post by Pumalite on 2007-12-06
Do you have a Linux system running?

---

### Post by Pumalite on 2007-12-06
If you do:
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1

---

### Post by Mark_in_Hollywood on 2007-12-06
Will this keep the drive permanently mounted? That is: will it now mount at power-up?

Please see the screenshot, is this the way that Ubuntu as an operating system wants to see the drive?

---

