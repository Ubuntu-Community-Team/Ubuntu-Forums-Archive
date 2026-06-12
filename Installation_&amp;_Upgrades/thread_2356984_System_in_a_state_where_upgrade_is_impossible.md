---
title: "System in a state where upgrade is impossible"
date: 2017-03-28
forum: Installation &amp; Upgrades
---

### Post by cmaurand2 on 2017-03-28
Hello,

I have a 14.04 server that I have kept up to date and is running the 4.4.0-64-generic (probably part of my problem.)  As i normally do, I start aptitude, press "u" to update the package lists then press "U" to perform the upgrade and this time instead of giving me a list of package to upgrade or install, it gives me a list 34 packages to be removed because they are no longer used like libboost and apache and, you know, everything it takes to make a production webserver run.  I messed something up somewhere.  Do I need to move the data to another machine and then do a wipe and reload?  What do you all need to see in order to help?  The last thing I installed was open-vm-tools-dkms before that was a kernel upgrade.

Thanks in advance,
Curtis

---

### Post by Bucky Ball on 2017-03-28
Welcome. Does it also give you a list of packages that will be installed, possibly updated replacements for what it is about to remove?

Please run this in a terminal and post the output.

```
lsb_release -a
```

---

### Post by cmaurand2 on 2017-03-31
Here is the output.

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty

```

It gives me a list of packages that it wants to remove which is just about everything.  It wants to upgrade a  packages


libc6
libcups2
libgnutls26
linux-libc-dev
multiarch-support

Don't know why cups is even installed.  I need to look at that some other time.

---

### Post by cmaurand2 on 2017-04-05
bump

---

