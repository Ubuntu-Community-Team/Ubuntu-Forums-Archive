---
title: "Unallocate Partitions: want to merge with existing ones: Gparted"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2013-07-15
Please see the screen shot. 

It has two "unallocated" partitions. 

I want to merge them with existing partitions, /dev/sda5 (or /dev/sda3).

How to merge both "unallocated" partitions (one of 9 GB and other of 1 MB) with one of the existing /dev/sda*.

Help.

---

### Post by slickymaster on 2013-07-15
[How to merge two partitions?]("http://askubuntu.com/questions/66000/how-to-merge-two-partitions")

---

### Post by Mark Phelps on 2013-07-15
Sorry, but basically you can't "merge" partitions this way.

The first unallocated space is only 1MB -- and you can't do anything with that due to rounding.

The second unallocated space is to the "right" of your swap partition. You can't "merge" it with any other partition because space has to be adjacent to a partition.

If you wanted to add this space to sda5, you would have to do the following:
1) Boot from a partitioning tool --Gparted LiveCD can do this, as can the Ubuntu installer
2) Move the swap partition to the right
3) Move the NTFS partition to the right
4) Expand the Ext4 partition to take up the new unallocated space

Be advised that this could easily take HOURS to do, and with any partitioning exercise, there is always the risk of losing data.  So, you should back up the stuff in the NTFS partition before you attempt to move it.

---

### Post by satyamM on 2013-07-16
Can I go like following way:

1. Do **swapoff** and **Delete** the **linux+swap** partition.
2. Extend /dev/sda3 to whatever I desire (probably extend it to last and **leaving 1 GB at last**)
2. Then allocate 1GB to swap space.

I'm not sure of anything. I'm just asking. Will deleting swap space in first step will cause any bad??

I am again attaching the screenshot for quick reference.

---

### Post by oldfred on 2013-07-17
If you delete swap and recreate it, you also then need to update the new UUID in fstab.
       sudo blkid -c /dev/null -o list

 sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

If you change the size of a Windows partition you need to run chkdsk for it to internally update its boot sector. Best to use Windows tools on Windows NTFS partitions but never to create new partitions.

---

