---
title: "libgtk1.2 support dissapeared with 6.0.6.1?"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by hulst on 2006-08-11
Hi,

I use ardour-gtk for my home recording. I've successfully installed it on my laptop (default 6.0.6), so I thought I'd replace my slackware with Ubuntu as well because I'm lazy. The stock 6.0.6 installation didn't do it for me, It had trouble showing my mount points during installation so that failed. But, hey, there's an updated ISO. That did install kubuntu-breezer on my box, but failed to install ardour-gtk.

```

root@moebius:~# apt-get install ardour-gtk-i686
<SNIP>
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ardour-gtk-i686: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                   Depends: libgtk-canvas1 (>= 0.1.1) but it is not going to be installed
                   Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
                   Depends: libgtkmm1.2-0c2a but it is not going to be installed
E: Broken packages

```
I installed kguitar just to test my apt-get. That went fine. I have multiverse and universe repo's switched on.

Is anyone aware of an issue with gtk? Is gtk1 phased out and is ardour not recompiled against gtk2.6?

Regards,
Sander

---

### Post by hulst on 2006-08-11
Ehm, never mind.

I only had main and restricted in the dapper-updates repository, and not in the dapper repo.

Pay better attention next time :mrgreen:

---

