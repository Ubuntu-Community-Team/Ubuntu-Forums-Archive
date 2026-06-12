---
title: "Stripped down server install CD?"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by pashdown on 2011-01-21
I normally use a PXE server for all my installs, but sometimes the box is not on the same VLAN as my PXE server.  I have been trying to build a custom server install CD, but I am trying to strip out all the optional and non-required packages to trim it down from 700MB.  I just want the bare minimum to get up and running and then get the rest from an mirror set by an included preseed file.

Determining what bare minimum packages are needed aside from the debian-installer packages is sheer torture.  Is there a way to pull this list, or a Debian/Ubuntu script that figures out requirements and downloads them into the pool?

Thanks in advance.

---

