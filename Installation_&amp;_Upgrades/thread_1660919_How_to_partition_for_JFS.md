---
title: "How to partition for JFS?"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Dimitree on 2011-01-06
Can someone help me out on how to partition ubuntu for JFS?
My HDD is 160GB and i can't find information for JFS Ubuntu installation setup?

---

### Post by deanjm1963 on 2011-01-06
Is this for a new install or wish to format a new drive?

If it's a new install you can select JFS from the file systems available or if it's to format a new drive you need to install gparted and jfsutils. The inbuilt "Disk Utility" formats pretty much everything except JFS.

Hope this helps.

---

### Post by Dimitree on 2011-01-06
Thanks deanjm1963,
I'm looking to install Ubuntu 10.10 64/32bit Desktop Edition and format the whole drive.

Unfortunately the Desktop Installer defaults to ext4 when using the "Erase and use entire disk option".
The only option for JFS is from the Advanced setup where i must manually partition the drive.

I just don't know how to partition it for JFS.

Do i need a swap? a "/"? "boot" partition?

Can someone help me out?
If you can simply tell me how many and what kind of partitions i need to make for JFS to work?

---

### Post by deanjm1963 on 2011-01-06
You need to do a manual partition.

You have 160gb ... how much you set up for root for the programs that you install is up to you.

I can only suggest a partitioning scheme.

/ = 20gb
/home = 136gb
swap = 4gb

It depends on how much ram you have as to how much swap you want, and wether you wish to "hibernate" or not. General rule of thumb is 1.5 - 2 x amount of ram if you wish to enable hiberation.

When it comes to manually partitioning you need to specify how much disk space you want for root, home, swap etc.

If you want 20gb for root ... type in 20000, then select JFS as file system, do the same for home, swap etc. Swap has it's own entry on the file system drop down menu.

Hope this helps.

---

### Post by Dimitree on 2011-01-06
Thank you very much deanjm1963!
This will do :)
Have a nice day/night.

---

### Post by deanjm1963 on 2011-01-06
You're very welcome. Hope it works out OK for you. If not, you know where to come back to ;-)

---

### Post by srs5694 on 2011-01-06
deanjm1963 has presented perfectly good advice. I'd just like to point out that partitioning choices, in terms of the number, size, and placement of partitions, don't really depend at all on what Linux filesystem you're using. You'd partition the disk the same for ext3fs, ext4fs, JFS, XFS, ReiserFS, or even Btrfs. The main exceptions to this rule would be if you've got a *really* big disk (like a RAID array) that's too big for certain filesystems. IIRC, ext3fs and ReiserFS both top out at 16 TiB, so you'd need a disk bigger than this to run into this problem. There could also be some subtle performance implications, and I'd avoid using ext2fs on any but very small partitions. For the most part, though, a partitioning system that works well for ext4fs will work as well for JFS.

---

