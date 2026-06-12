---
title: "Upgrade to Ubuntu 16.10 from 16.04 caused invalid filename extension error."
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by limiv on 2016-10-22
Hello, yesterday i upgraded to Ubuntu 16.10 and it froze during installation so i shut down my laptop after a while and got a purple screen after login which turned blue after a while. I launched a terminal and ran sudo apt-get update/upgrade and had a functional system once again, however the following error showed up when i ran sudo apt-get update:```

 N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```

And the following error shows up when i run sudo apt-get upgrade: 
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
N: Ignoring file '20auto-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```

Is there any way to fix this as it blocks me from updating/upgrading packages and the ubuntu software store has stopped functioning.

---

### Post by steeldriver on 2016-10-22
Are you sure that's actually an issue - the .ucf-dist suffix just denotes a configuration backup file

[http://manpages.ubuntu.com/manpages/xenial/man1/ucf.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/ucf.1.html)

AFAIK the message is just informational

---

