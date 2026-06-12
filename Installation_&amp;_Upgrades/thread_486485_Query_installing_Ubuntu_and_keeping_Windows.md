---
title: "Query installing Ubuntu and keeping Windows"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by durkhrod chogori on 2007-06-28
I need to know how much partition do I need to assign to Ubuntu when installing.

Currently, Windows is using 40% of the 1,024 MB of total memory.

Regarding disk space here are the stats:


Local disk C:    used (13.5 GB) available (42.4 GB)
Local disk D:    used (709 MB)  available (36.5 GB)


Thx in advance.

:)

---

### Post by kaltv on 2007-06-28
1,024 MB of total memory? You mean RAM? When you're accessing Ubuntu, Windows would be off so wouldn't be using the RAM, so no problems there. :)

As for partitions, well, apparently Ubuntu needs:
- at least 2 GB of space  for the bare minimum with barely any programs
- 5 GB is enough for you to install just about all the programs
- and a total of 10 GB would be nice if you want to actually add lots of files on it.

The simplest thing really would be to move all the stuff from your D: drive onto your Windows C: drive, then install Ubuntu on the entire D: drive.

You can still access Windows files directly from your Ubuntu desktop (it's auto-mounted), isn't that a joy? :D (the only problem is finding those files. Window's file system is confusing as heck, lol)

If you want to do a manual partition, you can set aside 5 GB or more for / on "D:", do at least 2GB for swap, and use the rest for /home. I have no idea what automatic partition does though. Manually doing partitions is one of the few things I Do know how to do. :(

Does that answer your question? :D

---

### Post by durkhrod chogori on 2007-06-30
> **kaltv said:**
> The simplest thing really would be to move all the stuff from your D: drive onto your Windows C: drive, then install Ubuntu on the entire D: drive.

Is the manual part. the third option of the three?

If so, how do I find D: drive when I reboot the machine?

How many gigs do you recommend me to install Ubuntu to?

Thx for helping out.

:)

---

