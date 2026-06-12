---
title: "boot directly into command line?"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by eppo on 2010-04-06
i just installed a fresh install of 9.10 on my amd64. when it starts it locks up right away. i know that this has to do with my nvidia card. i've had to do this in the past. but since it locks up i have no way to get into the command line. ctl-alt-F1 does not work.
is there a way to just have it boot right to the command line without loading up gdm?
thanks

---

### Post by oldfred on 2010-04-07
Have you tried to boot with the recovery mode. If you look at the difference in the grub menu it is the elimination of quiet splash and adds single. You can also edit the main boot line to remove quiet & splash and add single.

---

