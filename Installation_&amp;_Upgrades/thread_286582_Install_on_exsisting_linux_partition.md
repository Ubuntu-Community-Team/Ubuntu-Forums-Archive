---
title: "Install on exsisting linux partition"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Dieseldog on 2006-10-27
How do I install 6.06 on an exsisting linux partition and swap partition. I was only given the option of manual or automatic partitioning. My hard drive is already partitioned from a previous Vector install using Ext3, I'd like to leave the partitions alone.

---

### Post by black_rob on 2006-10-27
Download a copy of the gparted live cd, and resize the existing partition.  Assuming you have the disk space, you should be able to shrink your vector partition then create a new partition for Ubuntu in the free space.

---

### Post by Herman on 2006-10-27
Do you mean you want to leave the Vector install ext3 and swap area alone and install Ubuntu over the top of it? (Overwriting Vector?).
If that's what you mean, then just reformat the Vector ext3 partition, or if you want to be sure, delete the partition and reformat the free space as ext3 again and install Ubuntu there instead.

Otherwise, I agree with black_rob, [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")
has the ability to 'move' the Vector ext3 partition, (after resizing your other partitions). Last time I checked, the version of GParted that Ubuntu uses doesn't yet have the 'move' functionality. At least not in 6.06.
I usually let the installer automatically set the same swap area again, so many Linux instalations can all share the same swap area. I'm told this is okay as long as we don't 'hibernate' an operating system and then try to boot another If you like to use the 'Hibernate' feature instead of shutting down, then each operating system will need its own swap area.

Regards, Herman :D

---

### Post by Dieseldog on 2006-10-28
I'd like to install over Vector using the same partition. How do I skip the partition step and go directly to the install?

---

### Post by black_rob on 2006-10-28
If you want to overwrite Vectore go with manual partitioning.  Don't change the actually partitions, just make sure the mount points are correct, and that it will format the partitions.

---

