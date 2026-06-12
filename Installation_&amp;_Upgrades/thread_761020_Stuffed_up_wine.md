---
title: "Stuffed up wine?"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Boltster691 on 2008-04-20
I tried to install wine by following the directions given on the website, and now once I try and open add/remove programs, it says 

"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

And when I try and delete the wine.list thing, it says I don't have permission.

Regards, Cameron.

---

### Post by erginemr on 2008-04-21
1. You should first try the simple way:
```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
```
from a terminal. If no error comes out, that's it. 

2. If it is just a "repository not enabled" issue, please follow:
[http://ubuntuforums.org/showthread.php?p=4756533](http://ubuntuforums.org/showthread.php?p=4756533)
[http://ubuntuforums.org/showpost.php?p=4756533&postcount=8](http://ubuntuforums.org/showpost.php?p=4756533&postcount=8)

3. Otherwise, the problem indicates a broken Debian package management (dpkg) database, and the following might help:
[http://ubuntuforums.org/showthread.php?t=496550](http://ubuntuforums.org/showthread.php?t=496550)
[http://ubuntuforums.org/showpost.php?p=3001962&postcount=10](http://ubuntuforums.org/showpost.php?p=3001962&postcount=10)

---

