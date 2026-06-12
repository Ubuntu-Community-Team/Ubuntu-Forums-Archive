---
title: "Task Manager And System Profiler Only Shows Half My RAM,"
date: 2011-12-31
forum: Installation &amp; Upgrades
---

### Post by birdfoot on 2011-12-31
In task manager, On the bar that shows my total RAM usage, it shows "x/938 MB", where "x" is the amount of ram currently in use by the system and the 938 is what task manager thinks my actual ram capacity is. System profiler and Benchmark shows 961296 kB total memory. I've had 2 GB of RAM on this machine for years and this never happened.

32 bit Lubuntu.

If any more information is needed please let me know!

Thanks!

---

### Post by Herman on 2012-01-01
What output do you get from the following command? 
```
sudo lshw | sed -n '/*-memory/,/*-pci/p' | head -n -1
```

---

