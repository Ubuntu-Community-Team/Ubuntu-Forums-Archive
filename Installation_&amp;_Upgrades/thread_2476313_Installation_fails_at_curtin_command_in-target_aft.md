---
title: "Installation fails at curtin command in-target after configuring apt"
date: 2022-06-22
forum: Installation &amp; Upgrades
---

### Post by cathans on 2022-06-22
Hardware: SuperMicro E200-8D with M.2 NVME SSD installed.

During the Live Install of 20.04 LTS, the installer fails during the curtin command in-target command.  I've looked at the logs, but there's so much data (some noise) that I can't find a glaring issue.

I've dropped into another terminal during the install and can see via lsblk it sees the nvme drive and has partitioned it with a lvm, but that's about it.

This setup (Super micro Mobo/ssd) has worked for me in the past, but something has changed over that last 12 months when we last did an install of this type of setup.

Any help on where to look/what to look for and maybe some clarity as to what the installer is doing at this step would be appreciated.

Thanks in advance.

---

