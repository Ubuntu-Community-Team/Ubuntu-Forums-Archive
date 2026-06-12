---
title: "[SOLVED] Get Error Message: No root file system is defined..."
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by VexVishnu on 2008-06-25
...while installing Ubuntu. The laptop I'm trying to install it on has no OS right now. When I get to the "Prepare Partitions" section of the install and click the "Forward" button I get the following error message: "No root file system is defined.
Please correct this from the partitioning menu."

When I click the "Back" button a little box flashes and it says, "Starting up the partitioner"

There are no partitions showing in box.
The buttons "New partition table", "New partition", "Edit Partition", "Delete partition", and "Undo changes to partitions" are all grayed out and can't be clicked.

The only button that works (or gets me anywhere) is the cancel button.

Does anyone know how to set up a partition prior to attempting an install?
Or does anyone know what to do in case they get this error message?

I read some of the other threads for people that had this problem, but most of them had windows and were setting it up so they could dual boot.

---

### Post by Rocket2DMn on 2008-06-26
You should select the option to install to the entire hard disk.  Otherwise you need to do manual partitioning, where you need to specify a root (/) partition and a swap (no mount point) partition.  If the LiveCD doesn't allow this, you can try the alternate install cd which uses a text based installer - don't worry, it's still easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.

---

### Post by avtolle on 2008-06-26
Hmm, from the OP's first post, it sounds like the drive is mounted. If he is using the Live CD, please minimize Gparted, and see if there is an icon on the desktop with some name, other than the normal two (Install and Examples, I believe). If so, right click on the icon, select "Unmount volume", and when the icon disappears from the desktop, maximize the Gparted window and try again.

---

### Post by VexVishnu on 2008-06-26
Thanks, I'll have to try that out. I'll post the results.

---

### Post by VexVishnu on 2008-06-28
> **Rocket2DMn said:**
> You should select the option to install to the entire hard disk.  Otherwise you need to do manual partitioning, where you need to specify a root (/) partition and a swap (no mount point) partition.  If the LiveCD doesn't allow this, you can try the alternate install cd which uses a text based installer - don't worry, it's still easy to use.  You can get it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.

I can't find the option to install to the entire hard disk. I don't know how to do a manual partition and it doesn't give me the option to. I don't have any extra cd-r's so I can't try the alternate cd.

When I click on GParted it said No device found... I think my hard drive might be corrupted... I really hope it isn't though...

---

### Post by Rocket2DMn on 2008-06-28
Hrmm, you may need to find a way to get your hands on the alternate cd since it has more options available during the install process (this is what I normally use).
It is possible that the hard drive is corrupt, but it might still be OK.  You can try specifically using the GParted LiveCD and see if it recognizes the hard drive, but again, you don't have any cd-rs.  Here's the link anyway - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
From the LiveCD, can you please post the output of
```
sudo fdisk -l
mount
```

---

### Post by VexVishnu on 2008-06-28
Thanks, I'll definitely give that a try.

---

### Post by VexVishnu on 2008-07-03
Well, it turns out my hard drive was corrupted. *le sigh*

Thanks to everyone for their help, I appreciate it!

---

