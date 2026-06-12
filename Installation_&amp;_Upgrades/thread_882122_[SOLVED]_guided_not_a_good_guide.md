---
title: "[SOLVED] guided not a good guide"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by hmotwell on 2008-08-06
i'm trying to install 8.04.1 on an old computer that had win98 on it & i deleted all dos parts w/ w98 fdisk.
have 512 mb ram & 20 gb hdd.
i boot from 8.04.1 alt cd & select guided use entire disk because i don't want w98 anymore.
it sets up an ext3 part for / & another for swap.
but install craps out during select/install software due to space issue.
i picked guided option since i assumed it would make part large enough on its own.
how do i override the size guided is picking & what would be a good size w/n my 20 gb for / & swap?

---

### Post by spiderbatdad on 2008-08-06
You should be able to select "use entire disk." If you manually set partition sizes swap only needs to be 1GB in your case...with 512 RAM. / should be at least 8, I would think...especially if you don't create a separate /home.

There is a screencast here on partitioning, and creating a separate /home, which can be useful, but isn't necessary.
[http://screencasts.ubuntu.com/taxonomy/term/54](http://screencasts.ubuntu.com/taxonomy/term/54)

---

### Post by wpshooter on 2008-08-06
I agree that it is not a very good guide.

That is why I always use the manual partitioning.

---

### Post by aysiu on 2008-08-06
I don't see how it could have run out of disk space on a 20 GB drive if you told it to use the entire disk. Is your CD faulty?

---

