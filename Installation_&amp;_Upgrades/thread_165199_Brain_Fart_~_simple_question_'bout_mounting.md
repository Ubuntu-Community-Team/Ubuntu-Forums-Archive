---
title: "Brain Fart ~ simple question 'bout mounting"
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by bbbooolllooo on 2006-04-24
What's the easyiest way to determine the root partition before mounting?
seems like a catch 22 if you need to mount prior to using the df command in order to see mouint points.  

I have couple of drives from a failed server installed that I need to snag some files from:
```

user@me:/dev$ sudo fdisk -l hde

Disk hde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
  hde1               1         851     6835626   83  Linux
  hde2             852       14946   113218087+   5  Extended
  hde5             852        1189     2714953+  82  Linux swap / Solaris
  hde6            1190        1797     4883728+  83  Linux
  hde7            1798        9092    58597056   83  Linux
  hde8            9093       14946    47022223+  83  Linux
user@me:/dev$ sudo fdisk -l hdf

Disk hdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
  hdf1   *           1           2       16033+  83  Linux
  hdf2               3         245     1951897+  82  Linux swap / Solaris
  hdf3             246         367      979965   83  Linux
  hdf4             368       14946   117105817+   5  Extended
  hdf5             368         428      489951   83  Linux
  hdf6             429         793     2931831   83  Linux
  hdf7             794        1401     4883728+  83  Linux
  hdf8            1402        3833    19535008+  83  Linux
  hdf9            3834        5049     9767488+  83  Linux
  hdf10           5050       14946    79497621   83  Linux

```

Am I correct that I can't df until after mount? Am I doing it wrong?

Feels like i'm forgetting something ](*,)

---

