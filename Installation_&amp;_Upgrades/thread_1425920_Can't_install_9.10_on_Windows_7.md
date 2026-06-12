---
title: "Can't install 9.10 on Windows 7"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by coolyus5712 on 2010-03-09
Have live cd & download, windows will not open files. Help

---

### Post by presence1960 on 2010-03-09
You have 2 options:

1. Install ubuntu to a dedicated partition (full install). You will first need to shrink Windows 7 from it's disk management utility. Before shrinking I would defrag at least once or twice and shut down system restore and paging file until after windows shrink is completed. Shrink windows partition. This will create unallocated space. Now you need to boot from the ubuntu Live CD. When you get to the partitioner window Prepare disk space you want to choose the use largest continuous free space option. The installer will use the unallocated space on your disk to set up ubuntu for you.

2. If you want to use wubi (install ubuntu inside windows) you want to boot into windows 7. Insert the ubuntu CD and navigate to the wubi.exe file on the CD. Double click the wubi.exe file and it will install wubi inside windows.

---

