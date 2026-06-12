---
title: "Problem of installing 8.04 lts in Windows7"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by rezaulkabir on 2010-03-08
While installing 8.04 LTS in my friend's machine which has Windows 7 installed, I found the dual boot option is not there after installation from within windows. If there is any particular trick to solve this problem, please help.

---

### Post by sikander3786 on 2010-03-08
> **rezaulkabir said:**
> While installing 8.04 LTS in my friend's machine which has Windows 7 installed, I found the dual boot option is not there after installation from within windows. If there is any particular trick to solve this problem, please help.

Are you using the WUBI Installer?

The better way to go around is to make some free space on the Hard Disk say 20 GB or whatever suits you. Leave it unallocated, then boot in to the Ubuntu Live CD. Select Guided - Use the largest contigious free space in the partitioner options and go through rest of the setup process. It will automatically install everything, will dual boot Windows and to the most it will be a lot faster than the WUBI install.

Regards.

Sikander.

---

