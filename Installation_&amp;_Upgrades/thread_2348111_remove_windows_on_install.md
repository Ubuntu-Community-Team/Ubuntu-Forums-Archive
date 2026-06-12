---
title: "remove windows on install"
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2016-12-31
Does Ubuntu 16.04 and 16.10 provide a path to completely wipe windows from the machine and only install Ubuntu on the installation of Ubuntu?
I couldn't find any clear information on Google.

---

### Post by ian-weisser on 2016-12-31
Yes.
If you so wish, the Ubuntu installer will reformat the entire hard drive. This will remove all traces of Windows from the machine.

---

### Post by Impavidus on 2017-01-01
See here: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

At "Installation type", choose "Erase disk and install Ubuntu". Note, as some people get this wrong, this will erase the entire disk, not just the C partition. If Windows tells you you also have a D or E drive located on the same physical disk, those will be erased too.

Or choose "Something else" for manual partitioning, if you feel up to that job.

---

