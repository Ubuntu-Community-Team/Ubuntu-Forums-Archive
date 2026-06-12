---
title: "Logical partitions"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kernco on 2009-02-27
I've noticed that when doing manual partitioning in the installer, it now defaults to logical partitions after the first one.  Is there a reason it does this now?  I've never used more than four partitions, so I've always made them all primary.  Is there an advantage to having logical partitions even if you're not going to have more than 4 partitions?

---

### Post by cariboo on 2009-02-27
There is no advantage to using logical partitions instead of primary partitions. The reason I use manual partitioning, is so that I can set the partitions the way I want, I don't pay any attetion to the defaults

Jim

---

### Post by Gina on 2009-02-27
I prefer manual partitioning - I like to have full control even when installing on a small HD.  In which case I use three primary partitions for / /home and swap.  I use a separate /home partition so that I can reinstall the OS without losing my settings.

---

### Post by kernco on 2009-03-02
I partition my system the same way. The reason I started this thread was mainly to point out the fact that new partitions now default to logical, when in previous versions the default has been primary. Since it seems like primary is preferred, why was this changed?

---

