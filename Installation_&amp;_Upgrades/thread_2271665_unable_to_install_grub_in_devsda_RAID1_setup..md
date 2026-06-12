---
title: "unable to install grub in /dev/sda RAID1 setup."
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by klabacita on 2015-03-31
What has change?

   My current machine has ubuntu 12.x LTS and is been working some time without ant issue 3 HD RAID1+spare.
   Now I got a new machine amd 8 core, 3 HD 1TB each.
   I continue with the traditional setup raid1 2 HD+1 spare.

   /boot 536MB
   / 999GB
   swap 666MB(rest)
   Raid1 /dev/sda /dev/sdb

    Everything looks good but once I got the question about if I want to install grub on my system I say YES, and boom error with /dev/sda.

   'Unable to install GRUB in /dev/sda' Executing 'grub-install' /dev/sda' failed.
   This is a fatal error.

    I have read some docs but cannot see any light.

    What is wrong with my process?

   Thanks!!!

---

### Post by ryan151 on 2015-03-31
Mine did something similar a long time ago.

Have you tried boot repair?

It might work I am not sure.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

