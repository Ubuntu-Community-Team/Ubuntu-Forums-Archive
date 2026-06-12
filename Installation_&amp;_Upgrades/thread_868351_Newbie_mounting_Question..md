---
title: "Newbie mounting Question."
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Slug71 on 2008-07-23
Hey guy's i just did my first install of Ubuntu but not sure i mounted the partitions correct. 
I had Vista on before and didnt like it.
I have a 120GB Hdd and partitoned as follows

20GB Ext3 mounted as / for Ubuntu
10GB as Ext3 swap
40GB for Vista later(or back to XP)
60GB for Vista too  (as above)

Is that correct or should i have done more for Ubuntu??

Its on a Acer Extensa 4420.

---

### Post by iaculallad on 2008-07-23
> **Slug71 said:**
> 
20GB Ext3 mounted as / for Ubuntu

- This could accommodate your Ubuntu OS installation. Instead of just the /, you could add your /home partition.

> **Slug71 said:**
> 10GB as Ext3 swap

- Actually, the SWAP partition does not require any FS when formatted, it just serve as a "Secondary" RAM for your system. With that reserved amount of 10GB, that would be an overkill (you're wasting your disk space in here). How much physical RAM do you have? you could simply just use 1024MB as your SWAP and the remaining disk space would be added to your Ubuntu Partition.

---

### Post by Slug71 on 2008-07-23
Thanks, thats what i was thinking, I have 2 GB Ram DDR2.

What size partitions should i make for
/
and /home?

---

### Post by iaculallad on 2008-07-23
> **Slug71 said:**
> Thanks, thats what i was thinking, I have 2 GB Ram DDR2.

What size partitions should i make for
/
and /home?

With that amount of disk space you currently have, I'd say:

Root Partition /     = 15GB
Home Partition /home = 15GB
Swap Partition SWAP  = 2048MB

But, you could still increase your disk spaces for both / and /home.

---

### Post by Slug71 on 2008-07-23
Thanks very much

---

