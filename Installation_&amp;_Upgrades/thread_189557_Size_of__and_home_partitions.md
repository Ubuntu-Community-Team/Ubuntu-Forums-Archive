---
title: "Size of / and /home partitions"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-06-05
I'll be installing Ubuntu this evening.  I think I have one last question before doing the install:  I've read a lot about partitioning and whatnot, and I completely understand what to do.  I know I want to have a home directory separate from the OS partition.  The only thing I'm not sure of is how large to make each partition.  How are your partitions sized?  I just need advice/suggestions for that.

Thanks all, you've really been a great help thus far!

---

### Post by bluevoodoo1 on 2006-06-05
It's really up to you with your / and /home partitions. Most people make their swap twice the size of their RAM.


Here's what I have done.

I have an 80 gig drive...

I *had* the following partitions, but felt the root partition was too small...

5 gigs root, 2 g swap ~74 /home

so I changed it to...

10 gigs /, 2 gig swap, ~69 /home

When I had only 5 gigs, I only have about 1-1.5 gigs left, which got even smaller when I would compile a kernel (talking in the 100's of megabytes left). 

10 gigs is probably too much, since I have about 5 gigs left, but it pleases me well, and it like me, you're into installing lots of applications and don't want to worry about room... Perhaps 6-9 gigs for root will suit you?

---

### Post by aysiu on 2006-06-05
Read this:
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

