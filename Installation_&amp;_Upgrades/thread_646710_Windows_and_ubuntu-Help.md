---
title: "Windows and ubuntu-Help"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2007-12-21
I have installed ubuntu, but I am asked to install windows in the same machine, but vista does not want to install as long as ubuntu is there, I want to totally uninstall ubuntu, then install window after that install ubuntu how can I solve this problem ?
I have to have window.
Thanks

---

### Post by Pumalite on 2007-12-21
Get Gparted Live CD. Boot from it. Delete all partitions in your drive. Make new large partition of your whole drive formated ntfs. Install Windows. If Vista, you have to allocate space for Ubuntu with Vista partitioner first. If XP; boot Gparted again and resize your XP partition (right click on partition; use 'resize' from menu). Format the new partition ext3 if you want. Then install Ubuntu.

---

