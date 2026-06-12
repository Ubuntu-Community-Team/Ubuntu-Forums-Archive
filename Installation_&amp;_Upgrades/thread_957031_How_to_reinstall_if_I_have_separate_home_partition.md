---
title: "How to reinstall if I have separate /home partition?"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by JazonEsti on 2008-10-23
This is assuming I want a clean install or something happened to the upgrade. 

When I installed Hardy Heron, I created a separate /home folder. Suppose I upgrade to Intrepid Ibex how to I ensure my /home is intact and the partitions are mounted correctly? Also, will my settings (like Firefox bookmarks, OpenOffice configuration/templates) be saved? 

From what I recall when I installed 8.04, I installed Kubuntu in / and did something to /home (I forgot what it was). All I know is that yes, I now have a separate /home partition that mounts automatically. 

Thanks!

---

### Post by tuxxy on 2008-10-23
Go ahead and install, if its on a seperate partition it will be safe.

If it wasnt mounted then update your fstab wirth this line - note sda must be changed to your correct partition number of the /home, I just used sda3 for example

```
/dev/sda3 /home ext3 nodev,nosuid 0 2
```

EDIT: This may make more sense if you read near the bottom [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by C.S.Cameron on 2008-10-23
If you should have to reinstall, when you get to partitioning, select manual and then only select the root partition for formatting.
Installer should find the location of your home partition.

---

### Post by JazonEsti on 2008-10-24
Thanks! How about my bookmarks, contacts, etc? Will those be saved and automatically detected when I reinstall, or do I have to back up? Thanks!

---

### Post by Elviswind on 2008-10-24
Yeah, all your bookmarks, contacts, installed software config files are saved in subdirectories of /home, which, as you've mentioned, is in a separate partition and you will choose not to format that /home partition on reinstall.

---

