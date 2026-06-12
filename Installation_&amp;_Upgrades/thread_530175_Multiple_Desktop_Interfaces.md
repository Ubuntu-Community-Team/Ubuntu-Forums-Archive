---
title: "Multiple Desktop Interfaces"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by newbie2expert on 2007-08-20
Can I install UBUNTU, KUBUNTU and XUBUNTU at the same time. In other words how can i have Gnome, KDE and XFCE also with the ability to switch between them.

---

### Post by kerry_s on 2007-08-20
sure, but your chances for a screw up increases 3 times. installing each on a separate partion is better and safer.

---

### Post by newbie2expert on 2007-08-20
i remember seeing somewhere that said you could install them in synaptic and when u log on u could change them from the logon screen. just wanted to try that but dont know how. ill probably just select it from synaptic hoping it doesnt mess up my system.

---

### Post by vexorian on 2007-08-20
yes there are kde, xcfe and fluxbox packages in synaptic, once you install the package you can log off and then in the screen where you type your password there is a session button where you can pick the DE

---

### Post by kerry_s on 2007-08-20
> **vexorian said:**
> yes there are kde, xcfe and fluxbox packages in synaptic, once you install the package you can log off and then in the screen where you type your password there is a session button where you can pick the DE

yes, it's that easy, but sometimes they overwrite settings for other de's then chaos ensues and you end up with several broken de's that won't even let you log in to fix it.

if you must, i'm assuming you have ubuntu already->

sudo aptitude install xubuntu-desktop kubuntu-desktop 
or
sudo aptitude install kde xfce4

---

