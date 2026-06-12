---
title: "Upgrade to 5.04"
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by seti@tquadrado.com on 2005-03-13
Hi,

i have the stable version, but i'd like to try the new one.
Can i upgrade, or have i to re-instaal everything new ?

Thanks in advance,

-- 
pedro mg

---

### Post by Hackmo on 2005-03-13
[QUOTE=seti@tquadrado.com]Hi,

i have the stable version, but i'd like to try the new one.
Can i upgrade, or have i to re-instaal everything new ?

Thanks in advance,

-- 
pedro mg[/QUOTE]
 Just follow this guide

[http://www.ubuntuguide.org/#upgradewartytohoary](http://www.ubuntuguide.org/#upgradewartytohoary)

make sure you backup first.

---

### Post by bored2k on 2005-03-13
[QUOTE=Hackmo]Just follow this guide

[http://www.ubuntuguide.org/#upgradewartytohoary](http://www.ubuntuguide.org/#upgradewartytohoary)

make sure you backup first.[/QUOTE]
 If you had removed ubuntu-desktop, some stuff might not work as they were meant to [it gets removed if you try to remove packages that came with the warty installation].

---

### Post by Insanely on 2005-03-13
Just remember hoary uses x.org and not xfree86. For myself I just copied my /etc/X11/XF86Config-4 to /etc/X11/xorg.conf and the gui worked a treat.

---

### Post by bored2k on 2005-03-13
[QUOTE=Insanely]Just remember hoary uses x.org and not xfree86. For myself I just copied my /etc/X11/XF86Config-4 to /etc/X11/xorg.conf and the gui worked a treat.[/QUOTE]
 For some reason I didnt think of this when I installed hoary ... grr

---

