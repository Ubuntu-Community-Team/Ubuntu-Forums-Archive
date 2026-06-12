---
title: "Can you use some of your hd as ram?"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by 4an1 on 2011-03-16
can this be done on ubuntu, if so how well does it work?

---

### Post by kagerato on 2011-03-16
No, not exactly.  By definition, hard disk storage will never be RAM.  It will never perform as well as RAM, either.  It's designed to be cheap and to persist even when the machine is off.

However, you can use hard disk storage for swap.  Swap is a set of otherwise-unused blocks that become reserved on the device for paging out data that would otherwise be held in RAM.  The operating system kernel (Linux, in this case) makes the decision as to when and what data should be paged in and out of the swap file (or partition).

While swap technically expands the total amount of storage available to running programs, for maximizing performance you actually want to avoid using swap as much as possible.  Hard disks are about a thousand times slower than RAM in terms of latency, and often not much better than that in throughput.

If you'd like to learn more, please read these:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)
[http://www.linux.com/archive/feature/113956](http://www.linux.com/archive/feature/113956)

---

