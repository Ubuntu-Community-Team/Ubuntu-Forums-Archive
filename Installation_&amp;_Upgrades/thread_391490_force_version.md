---
title: "force version"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by falkenberg_cph on 2007-03-23
Hi
How do i force a particular version of af program. I have manually installed a program called Csound5.05, but the debian in synaptic is 4.23 - the update manager will overwrite csound5.05, how can i avoid that?

Thank you
Carsten

---

### Post by wonk-o-matic on 2007-03-23
If you didn't install the package, your package manager won't know about the manually installed software.  

If you did install the package, you could remove it and redo the manual install, or you could "pin" the version.  If you go that second route, maybe google a little bit on something like "pin debian package".

---

