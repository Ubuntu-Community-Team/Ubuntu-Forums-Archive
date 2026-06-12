---
title: "Unable to install gnome-shell in 15.04"
date: 2015-04-30
forum: Installation &amp; Upgrades
---

### Post by chris.ribal2 on 2015-04-30
Hey Guys,

in version 14.10 i used gnome-shell 3.14 from the official gnome3 ppas.

After upgrading to ubuntu 15.04 yesterday i tried to reinstall gnome-shell from the official ubuntu repositories, as i read that gnome 3.14 is included in the official ppas now. Although i get an error of missing dependencies if i try to install gnome-shell, gdm or other related apps, for example:

```
gnome-shell : Depends: evolution-data-server (>= 3.7.90) but it is not going to be installed
E: Unable to correct problems, you have held broken packages
```

If i try to get that held broken packages using ```
dpkg --get-selections | grep hold
```, but there seems to be no held package.

What can i do to fix that? Is there an error in the ubuntu ppas or in my package system?

Greetings

---

### Post by dino99 on 2015-04-30
i get no issue with the gnome3-team/staging ppa here on vivid i386 (no other gnome ppa)
maybe you will need to use ppa-purge first , then update again before upgrading the staging packages

---

