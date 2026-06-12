---
title: "I've installed from source, but Synaptic think i've still old version."
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by darck on 2008-01-05
I've just installed pango-1.19.2 from source by `./configure; make; make install'
Everything went correct. I need this package to install the newest libwxgtk, which need new pango.

Now i want install libwxgtk from repository , but it says there is conflict, because i have pango-1.18.2 (which is no true anymore) and it ned at least 1.18.3.

How to update information which synaptic has about current version of my pango. (I couldn't upgrade libpango through synaptic, because there wasn't any upgrade available. I had to download source made for debian from pango.com)

(i need libwxgtk to install deb package of Code::Blocks compiler)

---

### Post by oldos2er on 2008-01-05
Uninstall the old pango using Synaptic. You may then need to reinstall the newer one.

---

### Post by darck on 2008-01-05
problem is that libpango has too many dependencies to uninstall it. Synaptic would have to uninstall 30 other programs before installing libpango (together with gnome)

---

### Post by darck on 2008-01-05
i installed package as .deb, thanks to checkinstall program, but now have problem - gnome doesn't work. I need to undo my changes. Install oryginal ubuntu 7.1 libpango1.0-0 library. How to do that if synaptic thinks it's already new version installed???

---

