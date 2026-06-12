---
title: "Uninstalled Python - whole system disappeared"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by brucem9999 on 2010-01-29
Every time I booted in 9.10, Python requested a password. I didn't plan to do any programming very soon (I'm new to Linux, although I know Unix) because I'm just learning the shell, etc, so I decided to uninstall Python through the Package Manager. I selected all of the installed Python modules and when I clicked "Apply" I was informed that there was one module (Python minimum something) that would seriously effect the whole system, so I unchecked that module and then ran the uninstall.

When it completed, Firefox was gone, the two music players I had installed where gone, I couldn't log out and when I try to reboot I get a message "Ubuntu is running in low-graphics mode" and I go through several other menus, but I still can't get the system to boot.

I assume a reinstall is in order, but should I "clean up" any of the remaining Linux modules/partition? And what's the best way to do that?

---

### Post by oldfred on 2010-01-29
It is just about impossible to recover from an uninstall of python as major parts of Ubuntu run on it (if you have to there may be ways using a liveCD and chrooting). It should have given you a very long list of things it was uninstalling. You may not even have network as that often depends on python. If you have any data to recover you can use the liveCD to copy data. If you have a separate /home you will not lose those settings.

You should use manual install and choose the existing partitions, otherwise it will create new partitions and leave the old install and its space on the hard drive. This will erase everything installed before in the ubuntu partitions. I do not know if you can reinstall over the existing without reformatting.

---

