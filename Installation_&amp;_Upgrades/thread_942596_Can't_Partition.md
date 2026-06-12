---
title: "Can't Partition"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by kaelonlloyd on 2008-10-09
I used this code to show my HD so i can access it
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs-3g -o nls=utf8,umask=0000

but now i want to partition my drive so i can have Linux and my files separate, but it wont let me partition it, the PC says it has no free space when i try to install linux, but i know it got 4 GB,
Gpartition says i got Memory left too but it still won't partition

is their anything wrong with the code or anything else that would prevent me from partition

---

### Post by mikewhatever on 2008-10-09
The 'code' you posted has nothing to do with partitioning.
One reason you can't modify a partition may be because that partition is mounted. Either unmount it first or use Gparted live cd.

---

