---
title: "Kernel 2.6.22-14 on hardy?"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by ursli on 2008-01-31
I did upgrade via apt to hardy, but still got the 2.6.22-14 kernel. I tought hady comes with the 2.6.24 kernel. Can anyone enlighten me?

---

### Post by mikewhatever on 2008-01-31
> **ursli said:**
> I did upgrade via apt to hardy, but still got the 2.6.22-14 kernel. I tought hady comes with the 2.6.24 kernel. Can anyone enlighten me?

The kernel is in Hardy's repositories, not sure what went wrong [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=hardy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-image&searchon=names&subword=1&version=hardy&release=all)

---

### Post by studentz on 2008-05-01
I do have the same issue. I tried to change to the new kernel  in grub but looks like it is not installed.

---

### Post by studentz on 2008-05-01
I do have the same issue. I tried to change to the new kernel  in grub but looks like it is not installed.

---

### Post by j2fraser on 2008-05-01
I had the same problem. I was having a bunch of crashes and system performance issues. I checked /boot and the 2.6.24 kernel entry was there, but it hadn't found its way into /boot/grub/menu.lst. I edited the latter, adding the appropriate entry, and presto, no more problems.

---

