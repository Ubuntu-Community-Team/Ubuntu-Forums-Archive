---
title: "Mounting /home Directory"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by whitetimer on 2010-01-29
HI All

If i do a clean cli of Ubuntu where i have kept the partition form a  previous installation and i have / & /swap, when the installation is complete, how would i mount my old /home partition ?

Many Thanks

:popcorn:

---

### Post by chaanakya_chiraag on 2010-01-29
I'm not sure, but I think you have to mess with fstab (/etc/fstab if I remember correctly)

---

### Post by Grenage on 2010-01-29
You can specify it in fstab (/etc/fstab).

---

### Post by darkod on 2010-01-29
Just to clarify, you have separate /, /home and swap partitions right? You want a clean install of Ubuntu but to keep using the existing /home?

Start the install process and in step 4 select manual partitioning. All partitions will be marked as Not Used. Click on each of them one by one, and then the Change button at the bottom.

For /
Change filesystem to what it was, ext3/ext4
Mount point to /
Tick the format box (to make sure old version is wiped)

For /home
Change filesystem to ext3/ext4
Mount point to /home
DO NOT TICK THE FORMAT BOX OR YOUR DATA WILL BE WIPED

For swap
Filesystem swap
Mount point swap
No format available for swap

That's it.

---

### Post by whitetimer on 2010-01-29
> **darkod said:**
> Just to clarify, you have separate /, /home and swap partitions right? You want a clean install of Ubuntu but to keep using the existing /home?

Start the install process and in step 4 select manual partitioning. All partitions will be marked as Not Used. Click on each of them one by one, and then the Change button at the bottom.

For /
Change filesystem to what it was, ext3/ext4
Mount point to /
Tick the format box (to make sure old version is wiped)

For /home
Change filesystem to ext3/ext4
Mount point to /home
DO NOT TICK THE FORMAT BOX OR YOUR DATA WILL BE WIPED

For swap
Filesystem swap
Mount point swap
No format available for swap

That's it.


Yes thats what i wish to achieve, so many thanks for that :D

---

### Post by darkod on 2010-01-29
One thing that wasn't mentioned, I don't know if it can work if you create different username. I have only done this when creating the same username in the new install because your home folder now is /home/username and that will remain same with the data inside.
Not sure if it can work if during the new install you create different username.

---

### Post by whitetimer on 2010-01-29
> **darkod said:**
> One thing that wasn't mentioned, I don't know if it can work if you create different username. I have only done this when creating the same username in the new install because your home folder now is /home/username and that will remain same with the data inside.
Not sure if it can work if during the new install you create different username.

Ok thanks for that, but i will be using the same name, so no trouble there ;)

Many Thanks

---

