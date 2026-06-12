---
title: "update stalled"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by jason13 on 2013-11-15
During the update cycle the process has stalled. This round of updates included an update to kernel version 3.2.0-56, which is the last package the terminal window has started. It's been stalled for at least 5 hours, I'm afraid to kill the process or reboot because I don't know what will happen on restart. What actions should I take so I don't fark my computer?

---

### Post by jason13 on 2013-11-16
To clarify, the updates have been downloaded and the hang up is in the installation of the updates. I can divine from the terminal that the kernel image is in the process of installing when it hangs up.

---

### Post by fantab on 2013-11-16
5hrs is bit too much to wait. Kill the process.

Open Terminal:
```
 sudo apt-get upgrade
```

---

