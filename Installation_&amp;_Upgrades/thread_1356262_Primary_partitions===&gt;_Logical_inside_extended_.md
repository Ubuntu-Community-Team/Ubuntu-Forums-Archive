---
title: "Primary partitions===&gt; Logical inside extended part.?"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by nitromanrc on 2009-12-15
When i first installed, I didn't think I would ever need more than 4 partitions, and didn't feel like dealing with extended/logical partitions for whatever reason. ANYWAYS...now I am thinking about installing a distro dedicated to video editing. so I have 4 Primary partitions, and I cannot, with the current config, add another. Is there a way to move 2 of my partitions into an extended partition? so I can make another extended one?

---

### Post by Mark Phelps on 2009-12-15
basically, no.  You can move partitions around, but you can't move them into, or outside of, an Extended partition.  You would have to shrink the partitions you have to make room.  Move them to make them all adjacent to free up continuous space on the drive.  Then, copy off the partitions you want to save.  Create the Extended partition in their place.  Create two new partitions inside that.  And then copy the information back from those two partitions.

And even then, in Linux, that will change the "dev" associated with the partitions, so you may have to make boot and/or fstab changes to reflect that.

---

### Post by oldfred on 2009-12-16
You still only can have four partitions or three priamry partitions and and extended partition with many logical partitions. All the logical have to be in the one extended and have to be contiguous. 

You can shrink all your partitions, move them left, back up sda4 and delete it and recreate as a extended partition.

A new hard drive may be easier. You will have trouble creating new space regardless of how you do it.

An aside, in reviewing some old threads I did find where meierfra (who was a prime contributor to the boot_info_script) moved a windows install from an extended partition to an available primary using sfdisk and a text file.

---

### Post by nitromanrc on 2009-12-16
Yeah I guess I will just use another hdd. I was thinking of RAIDing anyways, so I don't lose any data. I guess I will back up my data, then reinstall and repartition. That will be good. Thanks guys!

---

### Post by oldfred on 2009-12-16
Raid does not prevent loss of data. When you accidentally delete it you delete it from both drives. Raid is for servers to maximize uptime. Good backup are the best way to prevent loss of data.

---

### Post by nitromanrc on 2009-12-27
don't lose any data to disk failure**.... RAID1, mirrored

---

### Post by phillw on 2009-12-27
> **oldfred said:**
> Raid does not prevent loss of data. When you accidentally delete it you delete it from both drives. Raid is for servers to maximize uptime. Good backup are the best way to prevent loss of data.

+1

Phill

---

