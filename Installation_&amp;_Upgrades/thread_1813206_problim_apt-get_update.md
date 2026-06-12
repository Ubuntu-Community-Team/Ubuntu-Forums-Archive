---
title: "problim apt-get update"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by M4D-C0d3 on 2011-07-27
[PHP]
root@r0x:~# apt-get update
Reading package lists... Done
W: Unable to read /etc/apt/apt.conf.d/ - DirectoryExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list.d/ - DirectoryExists (2: No such file or directory)
W: Unable to read /etc/apt/sources.list - RealFileExists (2: No such file or directory)  [/PHP]

---

### Post by luckyu on 2011-07-27
Seems like you have missing files. Go into the directories of the files and see if they exist.

---

