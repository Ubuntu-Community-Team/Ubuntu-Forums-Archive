---
title: "USB stick install running out of space"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by bwallen on 2010-04-06
I'm booting my server from a USB stick. It's working fine, but the root of my file system when booted only has about 100MB left. The USB stick itself has a little over 1GB free. How can I make / take up more space on the stick?

---

### Post by nerdzero on 2010-04-06
Hi bwallen,

You could try booting up with a live CD, insert your USB stick, unmount it, then run gparted to resize the partitions.

This documentation might help:  [https://help.ubuntu.com/community/HowtoPartition/ResizingPartition](https://help.ubuntu.com/community/HowtoPartition/ResizingPartition)

Backup any important data on your USB stick before trying this in case something goes wrong.

---

