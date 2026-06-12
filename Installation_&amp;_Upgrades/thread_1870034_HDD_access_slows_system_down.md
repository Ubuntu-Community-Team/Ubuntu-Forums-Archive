---
title: "HDD access slows system down"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by Gelupah on 2011-10-26
Hi,

I cannot seem to find a solution to this problem. Since my format and fresh install of 11.10 64bit, anything accessing the HD (copying files to and from USB drive, installing software, etc) slows my system down hugely. It feels like it's using up all the resources, to the extent of music becoming laggy, mouse becoming laggy in extreme times, and of course not being able to multitask.

I really have NO idea where to begin with this. Previously Ubuntu 11.04 (upgraded from 10.10) 32bit was running very smoothly, no such issues.

Do I need HDD drivers? What could be the cause?

Many thanks for any advice

---

### Post by jnorthr on 2011-10-26
assuming your system has a 64 bit processor, then you have installed the correct version of ubuntu. 11.10 has not been tested as well as one would expect so there may be issues with some combinations of hardware that are not handled well. This may or may not be the actual case as slow performance can be caused by many factors. Does your HDD have any led that winks when the o/s accesses the disk ? If so does it appear to be on most of the time ? I am thinking that your system may be doing a lot of swapping of bits like code, music, etc to the swap file on your HDD. A lot of swap will slow things down a lot. You can explore this topic by reading more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)  i think most of it applies to 11.10 as well.

---

### Post by Gelupah on 2011-10-27
Hi,

Thanks for the response and ideas, getting desperate here. I do have an LED that switches on when HDD is accessed. As expected, it doesn't do anything (but the occasional blip) when the system is doing nothing; but then if I copy files it gets heavily implicated and the system lags... Which is why I think it's a problem with actual file access, when it happens (and not continuous unnecessary HDD access), if that makes any sense?

I'll read up on the topic though, I'm open to any ideas and it's always good to know :)


> **jnorthr said:**
> assuming your system has a 64 bit processor, then you have installed the correct version of ubuntu. 11.10 has not been tested as well as one would expect so there may be issues with some combinations of hardware that are not handled well. This may or may not be the actual case as slow performance can be caused by many factors. Does your HDD have any led that winks when the o/s accesses the disk ? If so does it appear to be on most of the time ? I am thinking that your system may be doing a lot of swapping of bits like code, music, etc to the swap file on your HDD. A lot of swap will slow things down a lot. You can explore this topic by reading more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)  i think most of it applies to 11.10 as well.

---

### Post by Gelupah on 2012-01-27
Turns out the graphic card drivers (ATI) but messing about and were creating a bottleneck in the system somehow... Strange, but fixed with the installation of the latest ATI drivers !

---

