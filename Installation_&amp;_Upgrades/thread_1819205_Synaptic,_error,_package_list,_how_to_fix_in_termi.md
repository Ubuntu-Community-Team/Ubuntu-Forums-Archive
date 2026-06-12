---
title: "Synaptic, error, package list, how to fix in terminal?"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by pifactory3142 on 2011-08-05
When I open Synaptic Pckge Manager I get this error message:


Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


In terminal I run the sudo command sudo apt-get -f install and get the same error message.

How can I fix this? Thanks.

I'm running 11.4 xubuntu on an eeepc

---

### Post by oldos2er on 2011-08-05
```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
```

---

### Post by pifactory3142 on 2011-08-06
Ann, problem solved. Many thanks for taking the time and trouble to offer help. Another dud eeepc revived and out playing again.

Thanks again.

---

### Post by oldos2er on 2011-08-06
You're welcome.

---

