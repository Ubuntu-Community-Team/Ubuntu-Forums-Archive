---
title: "Error installing ubuntu (creating new partitions)"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by roberpreston on 2008-04-18
I'm trying to install ubuntu, when it makes new partitions gives me this message:
[IMG]http://farm3.static.flickr.com/2388/2422340937_2c474d18d6_o.png[/IMG]

I've looked in the forum for similar errors and found that should write:

> sudo fdisk -l

and looked like this:

[IMG]http://farm3.static.flickr.com/2026/2422340939_478969afd8_o.png[/IMG]

I need to preserve Windows partition.

What should I do?

---

### Post by dstew on 2008-04-18
From a Live CD boot, open a terminal and do```
fsck -t ext3 /dev/sda2
```This will look for errors on the disk.

---

