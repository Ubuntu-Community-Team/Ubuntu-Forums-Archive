---
title: "Getting the Lead Out of Linux"
date: 2009-04-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by int on 2009-04-29
A number of significant opportunities for performance improvements seem to be just over the horizon for Linux systems. OSNews regular lemur2 submitted an overview of the most important potential performance improvements to us.

One of the most popular freedom software programs in the world got a major boost this week. GCC 4.4 adds in lots of new features, the biggest of which is the [Graphite Framework]("http://blog.internetnews.com/skerner/2009/04/gcc-44-improves-open-source-co.html"). There are a number of new command line switches that provide better optimization. Any improvements in compiler optimisations have potential to achieve performance gains for a vast array of software.

The long-standing latency issues with the Linux ext3 filesystem, which most famously manifested itself as the much-lamented Firefox system-freeze problem, [might be finally cured]("http://lwn.net/Articles/328363/") by fixes which are due for inclusion in the upcoming Linux 2.6.30 kernel.

On a related note, the patches adopted in Linux 2.6.30 introduce many significant changes [affecting data security and Ext3 and Ext4 performance]("http://www.h-online.com/open/Kernel-Log-What-s-coming-in-2-6-30-File-systems-New-and-revamped-file-systems--/news/113157"). Support for the EXOFS and NILFS2 file systems is new, as is the cache for the AFS and NFS network file systems.

---

### Post by BGFG on 2009-04-29
a very nice read. Thanks.

---

### Post by gnomeuser on 2009-04-29
And GCC 4.4 was just imported to Koala (though not as the default compiler for all platforms as I recall). So hopefully we shall all benefit from the improvements.

Additionally there is a spec to move to i586 or i686 optimizations per default, this though is probably more about being honest as to what platforms we really do support (the threading libraries e.g. doesn't support anything below i486 or i586 - I forget which one). On the upside there are some nice optimizations available such as CMOV and friends which ix86 users will get the benefit of now.

---

### Post by Nullack on 2009-04-29
Intel is putting more devs onto GCC so lets hope we see more of the better ways ICC does optimisation coming into GCC for the future.

---

