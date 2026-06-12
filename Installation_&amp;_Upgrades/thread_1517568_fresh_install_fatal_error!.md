---
title: "fresh install fatal error!"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by wakabakalaka on 2010-06-25
Hi,

I installed a fresh copy of ubuntu on the previous linux partition but in the process I must have destroyed the GRUB >_<

At the end of the installation it said FATAL error failed to install grub, then it asked me where else I wanted to install it... I tried to select all other partitions but it kept saying failed. I chose continue without a bootloader.

Needless to say when I rebooted I was met with a blank screen with 1 word: GRUB and nothing else.

How do I manually install a bootloader?

I can boot with a live CD and I tried using the >grub program (after I installed it) but when I type the command: root (hd0,2) (where linux is) it said cannot find.

I have two harddrives which are in raid (so they appear as just one big chunk). not sure what to do!

---

### Post by mk1w86 on 2010-06-25
Could you please boot from the LiveCD and post the output of:

```
sudo fdisk -l
```

so we can see your disks and partitions.

---

