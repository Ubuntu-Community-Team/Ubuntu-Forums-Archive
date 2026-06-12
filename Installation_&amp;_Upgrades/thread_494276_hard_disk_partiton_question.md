---
title: "hard disk partiton question"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2007-07-06
I am using Xubuntu 7.04

i have a 20 gig hd, and it is a laptop.
I want to know how do i make my partition.

My current partition, but it seems like something wrong with it. I only have 10gig of space left in /
part /boot --fstype ext3 --size 100 --asprimary
part swap --size 96 --grow
part / --fstype ext3 --size 2048 --grow

Can anyone help me redo the partition.

I want the max space to store files and reasonable swap space.

---

### Post by Pumalite on 2007-07-06
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by dabl on 2007-07-06
Pumalite has pointed you to the GParted Live CD ISO download, which is the best tool to do your partitioning with. Burn the ISO image to a CD and you'll have the live CD to boot from.

As for a partition plan, you need 3 partitions, which I would allocate like this (I'm going to assume this is not a mega-powerful laptop):

for / = 6GB
for /{swap} = 0.5GB
for /home = all the rest of it

Set the bootable flag on the 6GB partition.  You do not need to format the partitions with GParted, but you can if you want to.

Next, boot your Ubuntu _Alternate Install _CD, and use "guided installation" to select the partition for each mount point (/, /{swap}, and /home) and you can set them to format at this time.  Follow the installation instructions as they appear, and you should end up with a Ubuntu system.  :popcorn:

---

