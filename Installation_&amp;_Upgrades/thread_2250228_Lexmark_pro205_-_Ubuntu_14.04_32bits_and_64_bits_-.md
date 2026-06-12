---
title: "Lexmark pro205 - Ubuntu 14.04 32bits and 64 bits - impossible to scan and print"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by ffa2 on 2014-10-27
Hello,


I passed since 2 days to try to print and scan with my lexmark pro 205. it  was work perfectly with lubuntu 12.04 32 and 64 bits but since the upgrade in 14.04 nothing work.

I tryed .Deb lexmark drivers (12.04) and the driver in .tr.gz. The .deb version warning an identification problem group in the installation procedure ("bin" group in place of "root"), but it seem not the problem.
In ubuntu 14.04, the driver with .sh installation (finle in .tar.gz) seem not work (nothing détection printer in the configuration software).

CUPS (1.7.2) write in error_log file:
1ere line : "Job stopped due to filter errors"
few lines later : PID XXXXX (/usr/local/lexmark/v3/bin/printfilter) stopped with status 113 (permission denied)

Before i arrived at this point, i meet the good right on the filter file, i replaced by the good group all files in the sub-directory lexmark  (root:root) and i have modified the CUPS configuration file in respect of the recommandation of this french thread  : [http://forum.ubuntu-fr.org/viewtopic.php?id=1668171](http://forum.ubuntu-fr.org/viewtopic.php?id=1668171)


For the scan, it is impossible to find the network scanner (through WIFI). Xsane start to search and he block. Is it a manual parameter file that i can indicate to Xsane the physical adress of my multifonction printer ?

Thank you for your help and sorry for my english,

Frederic


Lubuntu 14.04 64bits + zorin os 9 (ubuntu 14.04 32bits)

---

