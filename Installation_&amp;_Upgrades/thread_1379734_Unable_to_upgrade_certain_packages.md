---
title: "Unable to upgrade certain packages"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2010-01-12
I am unable to upgrade certain core packages, and I can't seem to find a reason.

Let me show you my apt-get and aptitude output:
apt-get:```

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
aptitude why-not:
```
patrick@patrick-laptop:~$ aptitude why-not linux-headers-generic
Unable to find a reason to remove linux-headers-generic.
patrick@patrick-laptop:~$ aptitude why-not linux-generic
Unable to find a reason to remove linux-generic.
patrick@patrick-laptop:~$ aptitude why-not linux-image-generic
Unable to find a reason to remove linux-image-generic.
```

There seems to be little on the internet concerning this return code for aptitude why-not. Any thoughts on how I can get my linux image upgraded?

---

### Post by slakkie on 2010-01-13
do

aptitude -s full-upgrade and post the output.

Ps. which version are you running (lsb_release -a)?

---

### Post by patman0623 on 2010-01-13
Ubuntu 9.10 64

My output (I changed the actual output on my last statement, I also have a conflict with wine but I know the reason behind that:

```
The following NEW packages will be installed:
  linux-headers-2.6.31-17{a} linux-headers-2.6.31-17-generic{a} 
  linux-image-2.6.31-17-generic 
The following packages will be REMOVED:
  lib32nss-mdns{u} winbind{u} wine{a} wine-gecko{u} 
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic 
3 packages upgraded, 3 newly installed, 4 to remove and 0 not upgrade
```

---

### Post by patman0623 on 2010-01-15
bump

---

### Post by slakkie on 2010-01-15
You can upgrade them safely from what I can see.

If you run aptitude safe-upgrade (I should have told you that in the previous post) prior to the full upgrade you will even have less to worry about.

---

### Post by patman0623 on 2010-01-15
Thanks a million - I can presume then that my previous version of the Linux image had been mismarked as "keep" in the package manager? I'm still a bit unclear even after reading the documentation.

---

