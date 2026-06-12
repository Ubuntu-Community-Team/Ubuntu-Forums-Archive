---
title: "Most of my disk space left out at installation"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by hodad on 2013-12-27
I recently installed 13.10, andmost of my disk was "left out" when I partitioned it.  I have a 1 TB drive, but most of it is separate from all my / directories (including /home).  Now the root and all subdirectories are full, while the rest of the disk sits unused.

What is the best strategy to "bring the unused diskspace in"?  I already formatted the unused space, and named it, but it's outside of the root directory, so I'm afraid that future downloads of system related files and apps will not have room.

Two screenshots are attached.

Thanks

---

### Post by deadflowr on 2013-12-27
You could try making a separate /home
This might give you an idea
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)
just a thought anyway.

---

### Post by hodad on 2013-12-27
Thanks for the link ... I was thinking of something along those lines.  My thought was just to move my existing /home subdir to the newly formatted (900MB) partition, but I'm sure it's not that simple.   I just found some instructions to do that at:

[http://www.maketecheasier.com/move-home-folder-ubuntu/](http://www.maketecheasier.com/move-home-folder-ubuntu/)

Sounds relatively easy; I think I'll give it a try...

---

### Post by oldos2er on 2013-12-27
Also see [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I assume you meant "newly formatted 900GB" not MB partition.

---

