---
title: "Cannot install lib32stdc++6 in Ubuntu 9.10 64 bit"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by Alex Farber on 2010-04-19
Trying to install Skype, I got an error message that lib32stdc++6 is not installed. This problem is described here: [http://ubuntuforums.org/showthread.php?t=1418902](http://ubuntuforums.org/showthread.php?t=1418902)
However, when I am trying to install  lib32stdc++6, it doesn't work:

```

alex@alex-64:~$ sudo aptitude install lib32stdc++6
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "lib32stdc++6"
Couldn't find any package whose name or description matched "lib32stdc++6"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by Alex Farber on 2010-04-19
Solved after system update.

---

