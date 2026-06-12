---
title: "Enabling 2GB RAM"
date: 2005-03-29
forum: Installation &amp; Upgrades
---

### Post by lawtech on 2005-03-29
I installed warty on a new i686 box with 2GB RAM. It popped up in 20 minutes on the first try! Love it!

The System Monitor..Resource Monitor shows "X of 885 MB" in Used Memory. Is that all the memory the kernel recognizes? How do I make use of the full 2 GB?

---

### Post by Bob D. on 2005-03-29
Most likely you did a default install with the i386 kernel. This kernel only supports 900MB of RAM. All you need to do is install a i686 kernel to get to all your RAM.

See here for more info and details: [http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-21.1496455883](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-21.1496455883)

Bob

---

