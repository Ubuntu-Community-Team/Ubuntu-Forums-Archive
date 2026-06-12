---
title: "Quick Question about VirtualBox"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by ablegreen on 2007-06-30
Hi, I'm installing Ubuntu 7.04 in VirtualBox. While installing, I got a popup saying that the disk space is getting low. Before, I created a VM, I selected the default 2gb dynamic disk space. Is it expanding as it should? Should I continue the Ubuntu installation, because it still seems to keep going?

---

### Post by tgm4883 on 2007-06-30
You say you did the 2Gb Expanding, but thats only going to expand to a max of 2GB.  You should allocate whatever you want to it (ie 20GB) and set it on expanding mode.  It will create a very small partition (under 50MB I think) then expand when necessary.  The partition will look like it is 20GB inside the VM, but the Virtual Disk file will be the actual space (ie < 20GB)

---

