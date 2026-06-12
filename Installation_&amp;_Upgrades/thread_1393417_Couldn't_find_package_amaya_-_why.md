---
title: "Couldn't find package amaya - why?"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2010-01-29
```
$ uname -a
Linux MyBox 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
```

```
$ sudo apt-get install amaya
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package amaya**
```

```
$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main

```

---

### Post by howefield on 2010-01-29
Because there is no such package, funnily enough ?

At least, not for your version.

[http://packages.ubuntu.com/intrepid/amaya](http://packages.ubuntu.com/intrepid/amaya)

Looks like it was only in the repositories for dapper, hardy and intrepid.

---

### Post by howefield on 2010-01-29
Download the .deb package here.

[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

---

### Post by MountainX on 2010-01-29
Thank you.

---

### Post by masuch on 2012-01-24
> **howefield said:**
> Download the .deb package here.

[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

thank you

---

### Post by oldos2er on 2012-01-24
Closed, necromancy.

---

