---
title: "How do I add new distros to GRUB, a GRUB question"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by brjoon1021 on 2006-08-26
I have my hard drive partitioned up so that I can install several Linux distributions. When I installed Ubuntu, it overwrote the MBR with its GRUB (it did not ask either). The distro that had its Lilo in the MBR now won't boot because I need to make changes to GRUB and that distro's Lilo so that the Lilo will be in the root partition not the MBR.

Is their a good and easy tutorial for this? I have wiki'd I have googled. I just need some basics: how to access the GRUB list from within Ubuntu, also, since I can not boot into some of the other distros, I need a way of finding their Lilo files and editing it so that Lilo is in the root partition for each distro. I am new at this and probably am making it sound more complicated. I am sure that you know what I mean.

Please help.

B.

---

### Post by Tomosaur on 2006-08-26
Try running 'sudo update-grub' in a terminal. This should scan your system and add / remove operating systems from the grub menu.

---

