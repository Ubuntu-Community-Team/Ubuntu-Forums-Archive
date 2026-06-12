---
title: "apt-get upgrade doing nothing"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by g.a. on 2012-10-19
hello,

I'm trying to upgrade from 11.10 to 12.04 but nothing happens. the GUI "update manager" tells me that I might upgrade to 12.04 but when I click on the button nothing happens.

From shell this is what I see:

> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


however I'm still in 11.10

What am I doing wrong?

Thanks,
g.

---

### Post by lisati on 2012-10-19
*sudo apt-get upgrade* won't upgrade from 11.10 to 12.04. You will need to use:
```
sudo do-release-upgrade
```

---

### Post by g.a. on 2012-10-19
oh, yes, it was a stupid question...

upgrade done, thanks

g.

---

