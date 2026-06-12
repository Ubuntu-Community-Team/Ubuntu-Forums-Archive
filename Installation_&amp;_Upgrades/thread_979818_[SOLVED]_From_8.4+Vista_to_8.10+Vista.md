---
title: "[SOLVED] From 8.4+Vista to 8.10+Vista"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by jesuisbenjamin on 2008-11-12
Hello forum,

Various bugs recently convinced me to make an attempt to install 8.10.
Currently installed OS are: Vista and Ubuntu 8.4. I backed up my Home in the Vista partition.
When booting on Live CD 8.10 for install, it proposes to arrange partitions as follow:

**Before:** 
/dev/sda1 0%
/dev/sda2 6%
/dev/sda3 18%
/dev/sda5 71%
/dev/sda6 3%

**After:**
/dev/sda1 0%
/dev/sda2 6%
/dev/sda3 18%
/dev/sda5 4%
Ubuntu 8.10 67%
/dev/sda6 3%

This is a bit confusing: does this mean my computer currently has  5 partitions? i thought i had 3 only: File system (8.4?), OS (Vista?) and RECOVERY (Recovery disk installed by Dell on laptop?).
I tried to select manual partitioning but couldn't do much. Besides seeing all the above was an indication i obviously don't know what's going on in my computer...
What i would like is to overwrite 8.4 with 8.10 and leave Vista and eventual Recovery disk untouched.
What should i do?

Thanks

---

### Post by jesuisbenjamin on 2008-11-15
I found my way out:

- Select manual when partitioning the disk. Ubuntu 8.10 shows as occupying 100% of the disk but don't be scared and click next.
- Select your current partition reserved to 8.4, click edit partition.
- Tick 'format' box, and ' mount to / '  in drop down box.
- Select swap partition, control it is reserved as swap space.

Go next. Your install should work fine.

---

