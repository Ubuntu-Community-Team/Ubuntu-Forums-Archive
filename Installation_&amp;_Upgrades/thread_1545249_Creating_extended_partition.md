---
title: "Creating extended partition"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by icarus035 on 2010-08-03
Hi all. Can someone please explain to me how to create extended ext3 partition using GParted? Every time I select "New" for unallocated space I can only create primary partition. Other options (extended and logical) are always greyed out.
Thanks!

---

### Post by Elfy on 2010-08-03
Is there already an extended partition - you can only have one extended.

---

### Post by icarus035 on 2010-08-03
No. Attached picture shows my current partitions. Basically I want to dual boot XP and Ubuntu. So my idea was to partition in the following way:

1GB - swap
10GB - home
10GB - root
30GB - ntfs (for XP)
450GB - this is the ntfs partition with all my data.

When I try to create the last partition (for root,  marked as "unaloocated" on the picture) it displays error something like "You cannot have more than 4 primary partitons". I am a bit confused about this now.

---

### Post by lechien73 on 2010-08-03
That's correct, so as forestpiskie said, you can only have one extended partition and that already exists as /dev/sda2.

You can have a maximum of 4 primary partitions, one of which can be designated as an extended partition. So creating another primary partition in the unallocated space would result in 5 primary partitions, which is not allowed.

I would suggest using GParted to reduce the size of your ntfs data partition. You could then move the home partition to there, and have root as a primary.

---

### Post by icarus035 on 2010-08-03
Thanks for the help!

---

### Post by rawlins02 on 2010-08-03
1) Start with no partitions, make the ntfs for Windows OS a primary partition (/dev/sda1).
2) ntfs data partition is next primary (/dev/sda2). Pick a size that will leave enough for your linux extended partition.
3) Make the remaining unallocated space an extended partition, with logical partitions for root, swap, /home, and perhaps /usr.  If you planned right you will have the amount in /home you wanted. If not resize sda2.

---

