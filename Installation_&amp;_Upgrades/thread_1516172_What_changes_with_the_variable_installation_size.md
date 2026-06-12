---
title: "What changes with the variable installation size?"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Etyx on 2010-06-23
Using the Wubi installation you get to choose the desired installation size so I'd like to know in what way exactly the size is going to affect the OS.

I guess it just changes how much stuff you will have pre-installed at your first boot but perhaps there is more to it.

---

### Post by darkod on 2010-06-23
No, I think you still end up with the same default packages installed.
Wubi works inside windows, sort of virtual from an image file on the disk. The size you select limits the size of that image file, and how much space you will have available working from wubi as a linux filesystem.
I think wubi is still able to see the data on your ntfs partitions, so in a way the size you select is not the max you can see and use.

But for wubi it will simulate a hdd size. If you select 20GB it would be similar like installing full ubuntu to a 20GB disk/partition.

Does that make sense? :)

---

### Post by Etyx on 2010-06-23
Right now, I'm using ubuntu next to Win but I'm going to switch completely to ubuntu pretty soon. I also mounted my Win partition and can access everything.

So after formatting everything and only re-installing ubuntu will I still be prompted to choose the size? According to your explanation, it wouldn't really matter at all if I got that right, or would it?

---

### Post by darkod on 2010-06-23
I didn't quite understand. When doing a full ubuntu install (not wubi) on its own partition with its own filesystem, you still decide how big that partition is.

During the install you can use one of the automated methods, or manual partitioning which is always preferred. That way you set up your partitions exactly how you want them. Also, if setting up separate /home partition you have to use manual partitioning.

Separate /home is better because it allows you to do clean install to the / partition but still keep your personal files and settings in the separate /home.

If you are dedicating the whole hdd to ubuntu and you want to use automated method, you have the Erase and use whole disk option. I guess it says enough about what it will do. Wipe the disk and use it for ubuntu, but the installer will decide on the size of the / and swap partitions.

If using manual partitioning and you can dedicate XX GB to ubuntu, manually you would create like:

primary partition, ext4, mount point /, size 15GB (10GB if you are really short on space)
logical partition, swap area, size 2GB or if regularly hibernating then 1.5 x RAM size
logical partition, ext4, mount point /home, size the rest

That's all you need and in future you can make clean installs on the / partition by keeping /home. But you have to use manual partitioning again and tell the installer which partition to use as what.

---

