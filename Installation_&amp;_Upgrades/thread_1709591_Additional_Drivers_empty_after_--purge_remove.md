---
title: "Additional Drivers empty after --purge remove"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Appé on 2011-03-18
Hello,

For some months ago I removed my default nvidia drivers and installed the drivers from nvidia.com. 
Now I regret this since I have troubles to boot after kernel updates, and I want to revert back to nvidia-current drivers in Additional Drivers. Since I guess these working best with the common kernel updates to Ubuntu 10.10?

Anyway, according to my .bash_history I can the commands below before installning the drivers from Nvidia.com. Now when I go into Additional Drivers I do not have any drivers available anymore? Before I had 3 different drivers to choose.

sudo apt-get --purge remove nvidia* nvidia-kernel-common nvidia-settings

Question: 
Howto restore Additional Drivers as it was when I installed ubuntu the first time?
Right now I could boot the new kernel if I reseted the drivers via recovery mode.

Thanks!

Specs:
Ubuntu 10.10
gfx-card: Nvidia 8800GTS 640mb


EDIT - SOLVED:
[https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)

---

