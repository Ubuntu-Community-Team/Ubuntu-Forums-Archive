---
title: "Installation failure on 8.04.1 for Vostro 400"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by corp.linux on 2008-07-10
Downloaded 8.04.1 desktop earlier today and burned a CD using INFRARECORDER.  Installed fresh 250 GB hard drive (removed old Windows drive), inserted the CD and booted.  Get the following messages:

* Starting anoc............                   [OK]
* Starting deferred execution scheduler atd   [OK]
* Starting periodic command scheduler crond   [OK]
* Checking battery status...                  [OK]
* Running local boot scripts (/etc/rc.local)  [OK]

Then the system hangs, any suggestions?

---

### Post by Vivaldi Gloria on 2008-07-12
I suggest you try these in the order given below:

1) Have you checked the md5 sum of the cd? Make sure that it is ok. If not, download and burn again. Burn very slow.

2) Download & try the alternative desktop cd.

3) There is a last option which works most of the time. Download minimal cd from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This is just a 10 MB cd which downloads everyting from the net during install. So you can use it if you have a decent net connection. Use it to install a command line system. After you install it you can use the command

```
sudo apt-get install ubuntu-desktop
```

to install the full ubuntu desktop.

---

