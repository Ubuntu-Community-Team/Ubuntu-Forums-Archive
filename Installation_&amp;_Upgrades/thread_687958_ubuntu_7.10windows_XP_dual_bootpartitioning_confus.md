---
title: "ubuntu 7.10/windows XP dual boot/partitioning confusion"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2008-02-04
Hi

I am trying to do a dual boot of Ubuntu 7.10 for the first time.
Eventually I need to create a shared area that I and others
(Windows XP users) can both use but to keep things simple
I did a dual boot without creating a shared area
(I have never partitioned a disk before).

Windows XP seems to use about 10G but even after multiple defragmentations
it is spread out over appx.  40G.  Also, the windows defragmentor only
references about 140G even though I have a 160G drive.
So when I installed ubuntu 7.10 I (thought I) set it to use 95G of memory
(68%) for Linux.
This was selected by moving an arrow selecting between 0 and 100 %.
This didn't give me the result I expected.  Windows does run but when I do a
df from ubuntu I see only about 60G of disk space (about 68% of 95G)
and it seems I have a volume? of approximately 95G.

So now I am confused.
I assume that what I should do is run some kind of partitioning program and
partition my 160G drive into:
40G for windows (I would like it to be less, say 30G).
30G for Linux (I would prefer 40G).
90G for a shared space accessible by Windows and Linux.

I downloaded and burned the system rescue CD  systemrescuecd-x86-0.43.iso.
Its documentation says I can use it to do the partition.

Must I partition my disk into volumes?  And what is a volume anyway?
Any explanation as to what things I did wrong much appreciated.
Any explanation as to what I do now even more appreciated.

Should I simply reinstall ubuntu 7.10 again?
And if so what do I do different?
Should I simply do a manual partition of the disk?

Thanks

Ralph Boland

---

### Post by Odrodzona-Sarmacja on 2008-02-04
Partition the disk using gparted livecd. Gparted is Partition Magic for linux. It's free. Primary partition for windows, the rest as logical partitions. Create the common space in fat32, as xp and ubuntu have no problems with recognizing it. Also remember to make three partitions "/", "/home" and "/swap" on the linux part. "/" is the part with linux's "pogram files" and "windows" directories, so give it 8gb. "/home" is the part with all settings you are going to make will be saved and your "download" directory will be placed. If you use it just for settings, then 4 Gb should do the trick. "/swap" is something for memory like that virtual memory swap file on windows, which on windows never was bigger then 130mb anyway... so give it 512gb out of joy of it :D

After reformating, install as first windows on the primary partition, then go with ubuntu installation.

Good luck!

---

### Post by Ralph Boland on 2008-02-05
Thanks.
I followed the  instructions you gave below and now have the dual boot of machine working.
I still have / and /home on the same partition but I'll sort that out another day.

Regards

Ralph Boland


Partition the disk using gparted livecd. Gparted is Partition Magic for linux. It's free. Primary partition for windows, the rest as logical partitions. Create the common space in fat32, as xp and ubuntu have no problems with recognizing it. Also remember to make three partitions "/", "/home" and "/swap" on the linux part. "/" is the part with linux's "pogram files" and "windows" directories, so give it 8gb. "/home" is the part with all settings you are going to make will be saved and your "download" directory will be placed. If you use it just for settings, then 4 Gb should do the trick. "/swap" is something for memory like that virtual memory swap file on windows, which on windows never was bigger then 130mb anyway... so give it 512gb out of joy of it

After reformating, install as first windows on the primary partition, then go with ubuntu installation.

Good luck!

---

