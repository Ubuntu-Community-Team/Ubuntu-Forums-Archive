---
title: "[SOLVED] Partition problem: whole Windows partition now called &amp;quot;swap&amp;quot;...uh oh"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Emily on 2008-04-05
I am trying to install Ubuntu as a dual boot on my Windows machine (I reinstalled Windows XP today too--spring cleaning, as it were).

When I got to the partitioning part, I tried to create a swap partition by entering a partition size and choosing "swap" as the type, but it seems to have decided my entire Windows partition is swap. This seems ... bad. I quit the installer and am back in the Ubuntu live environment.

Right now I have two partitions, a small FAT32 partition that contains Windows recovery stuff, and a large partition that has Windows. What I'm trying to get to is a ~75gb partition each for Windows and Ubuntu, swap, and a large FAT32 partition to share data between them. Maybe a separate /home as well?

I've tried to look for help with this problem online, but in tutorials, people seem to be starting with a lot of unallocated space. Since I have no unallocated space, it's all the Windows partition, I seem to be seeing different things.

Any suggestions of what to do? I'd prefer to find a way out of this without ruining my Windows installation, but since I just reinstalled it today, what the heck.

---

### Post by logos34 on 2008-04-05
You need to shrink sda2/windows partition down first, then create an ext3 / and /swap out of the freed space.  You don't need to have a fat32 shared data partition--fs-driver in windows will  allow you to read/write to linux ext3, and ntfs-3g in linux allows you to write to windows.

If you want a separate /home too, you'll need to create an **extended** partition out of the freed space (because there's a 4 primary partition limit) and put all your linux partitions inside as logical partitions.

---

### Post by Partyboi2 on 2008-04-05
You will need to resize the windows partition down. You can do this by using the partition editor (System>Admin>Partition Editor) on the live cd. After you have resized the windows partition you will have unalocated space which you can use to create your swap and ubuntu partition (Ext) and your /home partition if you decide to have one.

---

### Post by jpkotta on 2008-04-05
I recommend a /home partition.  See [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) for some tips about relative sizing of partitions.

---

### Post by Emily on 2008-04-06
Turns out that my previous mistake had screwed up my Windows installation, so I did have to backtrack, but after that, this advice worked like a charm. Installed Windows, shrank its partition, created / and swap, and made /home a logical partition in /. I think my mistake was in arbitrarily attempting to create the swap partition first--once I did that, it thought that whole huge partition was swap, and I couldn't fix it.

Thanks for all the good advice.

---

