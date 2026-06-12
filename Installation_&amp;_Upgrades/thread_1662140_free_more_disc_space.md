---
title: "free more disc space"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by net fun on 2011-01-07
I reloaded my lap top after crash with 9.04.  Must have not made enough disc space available to get upgrades (system says 46.9MiB).  System says have 993.2MiB hardrive memory.  Can someone please walk me through freeing up more disc space?  Thank you!

---

### Post by drs305 on 2011-01-07
I'll assume you know the difference between hard drive space and memory. 

To clean up hard drive space, you can get empty your trash bin and also remove packages from the system which are currently stored but not being used.

This command will empty your package cache.
```
sudo apt-get clean
```

You empty your trash bin by right clicking on the icon and selecting the option to empty it.

If you have deleted large files as root, you also should empty the files in /root/.local/share/Trash. These will also continue to take up space until removed.

If you are wondering where your free space has gone and don't know, take a look at this guide. It provides ways to locate what is taking up the extra space and how to eliminate it:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

