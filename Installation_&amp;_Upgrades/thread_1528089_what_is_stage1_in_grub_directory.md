---
title: "what is stage1 in grub directory"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2010-07-10
What does stage1 and stage2 refer to in grub folder.

---

### Post by confused57 on 2010-07-10
This explains it quite nicely:
[http://members.iinet.net.au/~herman546/p15.html#orientation](http://members.iinet.net.au/~herman546/p15.html#orientation)

---

### Post by Zip247 on 2010-07-10
From [here]("http://www.dedoimedo.com/computers/grub.html")

 Stage 1 is located in the MBR and mainly points to Stage 2, since the MBR is too small to contain all of the needed data.

Stage 2 points to its configuration file, which contains all of the complex user interface and options we are normally familiar with when talking about GRUB. Stage 2 can be located anywhere on the disk. If Stage 2 cannot find its configuration table, GRUB will cease the boot sequence and present the user with a command line for manual configuration.

Stage 1.5 also exists and might be used if the boot information is small enough to fit in the area immediately after MBR.

The Stage architecture allows GRUB to be large (~20-30K) and therefore fairly complex and highly configurable, compared to most bootloaders, which are sparse and simple to fit within the limitations of the Partition Table. 


This applies to grub 1 or legacy grub.  For grub2 info see [here]("http://ubuntuforums.org/showthread.php?t=1195275")

:KS

---

