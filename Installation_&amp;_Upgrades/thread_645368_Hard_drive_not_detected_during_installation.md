---
title: "Hard drive not detected during installation"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by prakharprakash on 2007-12-20
Hi !

I am new to Linux and want to get started with Ubuntu 7.10. I am using HP dv2000 series laptop. I booted the Live CD and ran the installation. I am looking for a dual boot configuration with Vista.

So, I chose manual partition method and partition manager (on the next screen) showed two partitions - one vista and other HP recovery partition.

The problem is, it says "unknown" on disk usage for the primary partition ( the vista one---where i am trying on install Ubuntu as dual-boot) and as a result, it does not allow me to set partition size, etc and partition it. However, it detects the second partition perfectly.

I ran disk-check on vista and no errors popped up. What could be wrong ?

Thanks in advance

Prakhar

---

### Post by logos34 on 2007-12-20
Use vista's disk mgmt tool to shrink it, then install ubuntu in free space.  Defrag it beforehand.  Might also have to temporarily disble hibernation and/or swap.

---

