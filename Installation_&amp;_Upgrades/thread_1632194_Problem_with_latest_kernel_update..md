---
title: "Problem with latest kernel update."
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by charlie_b on 2010-11-27
I am using Ubuntu 10.04. I keep it updated regularly. This morning I installed a new linux kernel, the latest available update, via the Synaptic Package Manager. However, when the system was installing and configuring it it seemed to hang up and crash. 
As near as I can tell the problem occurred when grub.cfg was running. The new kernel seems to be in place, in the root directory. After I restarted, it is not in the grub boot menu. I am using the previous kernel at the moment and everything is working fine.
So, what would be advisable to do in this situation? I don't want to muck around and stuff up the system now while it's working okay with the current kernel. But I want to keep the system up-to-date.

---

### Post by Quackers on 2010-11-27
Welcome to UF :-)
If you are unhappy with the way the new kernel appeared to install, just go to Synaptic and enter in the search box the kernel number and uninstall the kernel and headers completely. There should be 3 items I think to remove. Then wait for the update manager to re-install them.

---

