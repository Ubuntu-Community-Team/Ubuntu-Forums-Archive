---
title: "advice on swap please !"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by maverick555 on 2010-10-25
I am switching from xp to ubuntu.Now i have following pc specification.
motherboard : 775i65g
Ram : 1.5Gb
video : intel integrated graphics controller 82865g.
hdd: 80gb
I know how to install in advance mode but, i want to know how much swap should i give?
and the mount space? if i install home partition different can i able to insall new ubuntu 11.04 when it comes?
thanks..

---

### Post by carl.davis on 2010-10-25
Hello,

The easiest partitioning scheme is simply a root partition and a swap partition. A good rule of thumb is to make your swap partition slightly larger than the size of your RAM. 

If you have a need to do something more complicated you can check out:

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by BouldRake on 2010-10-25
There is no right answer, it depends on your needs.

Personally, with 1.5GB ram, I'd go for a 3GB swap drive.

As a rule of thumb, 

2GB ram or less - 2*ram swap
4GB ram - 2GB swap
4GB to 16GB ram - 4GB swap
16GB - 64GB ram - 8GB swap
64GB - 256GB ram - 16GB swap

But, if you want to suspend to disk (hibernate), you need more swap than ram.


Putting /home on it's own partition is a bit more work, but it's worth it.  If you ever need to reinstall, decide to change distro, or anything, it's left untouched, and your config, files, and settings are retained.

With 80GB, I'd go:
10GB / 
3GB swap
Everything else /home

---

### Post by maverick555 on 2010-10-25
Thanks for all who answered.solved installing maverick.:):)

---

