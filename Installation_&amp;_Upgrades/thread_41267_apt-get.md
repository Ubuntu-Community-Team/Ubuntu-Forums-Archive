---
title: "apt-get"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by albazero on 2005-06-12
up until today my apt-get would work perfectly

but starting today every program i try to install i get

```
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
``` 

that  :-|

---

### Post by Xian on 2005-06-12
It's not a local problem. You may want to comment out those ftp.nerim.net repos from your /etc/apt/sources.list for the time being as they seem to be problematic at this point.

---

### Post by albazero on 2005-06-12
[QUOTE=Xian]It's not a local problem. You may want to comment out those ftp.nerim.net repos from your /etc/apt/sources.list for the time being as they seem to be problematic at this point.[/QUOTE]
 thanks that worked

---

