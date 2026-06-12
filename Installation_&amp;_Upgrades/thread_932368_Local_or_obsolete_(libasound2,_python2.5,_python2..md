---
title: "Local or obsolete? (libasound2, python2.5, python2.5-minimal)"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by alexgieg on 2008-09-28
Hi! I've noticed Synaptic showing these three packages in the "local or obsolete" category for a few months now:

[LIST]
[*]**libasound2** (1.0.16-0ubuntu0.1)
[*]**python2.5** (2.5.2-2ubuntu5)
[*]**python2.5-minimal** (2.5.2-2ubuntu5)
[/LIST]
Have them been removed from the repositories? If so, that's strange, since lots of other packages, including famous ones such as Amarok, or even Python itself, depend on them and wouldn't install without them. If not, what repository am I missing?

I'm running Ubuntu 8.04.1 with a handful o KDE apps thrown in, and I have all standard repositories enabled plus a few extra ones, such as Medibuntu's. The full list:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ hardy partner
deb http://packages.medibuntu.org/ hardy free non-free
deb http://dl.google.com/linux/deb/ stable non-free
deb http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
deb http://wine.budgetdedicated.com/apt hardy main
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
deb http://ppa.launchpad.net/team-xbmc-hardy/ubuntu hardy main
```

Any suggestion is most welcome.

---

