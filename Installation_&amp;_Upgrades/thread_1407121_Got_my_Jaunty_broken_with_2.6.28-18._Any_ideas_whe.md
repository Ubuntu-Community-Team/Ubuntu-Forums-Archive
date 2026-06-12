---
title: "Got my Jaunty broken with 2.6.28-18. Any ideas where to check?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by nicksukharev on 2010-02-14
I got a weird situation after 2.6.28-18 upgrade. After I restarted, I got just may be 15 modules loaded in the kernel with my mouse not functional (both USB and touchpad), network apparently not functional as well. I checked lsmod and found less than 1 page of drivers there with this list normally going for at least a couple of pages. I was unable to find anything suspicious in /var/log. Any ideas what to check? After I restarted back to 2.6.28-17, I got everything running no problem. Any hits?

---

### Post by nicksukharev on 2010-02-14
I think I know what it is - I was playing with iPhone kernel module and its install script seriously messed up my kernel.

---

