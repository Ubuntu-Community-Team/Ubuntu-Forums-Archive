---
title: "Forcing Package Removal"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by hysbyswr on 2009-11-17
Is there a way to force the removal of a package, without removing other packages that rely on the first?

For example, I would like to get rid of "swfdec-gnome".  Unfortunately, "gnome" and "gnome-desktop-environment" packages rely on "swfdec-gnome".  I would like to keep "gnome" and "gnome-desktop-environment", but remove "swfdec-gnome".

I have tried apt-get, synaptic, and aptitude, but they all tell me I need to remove "gnome" and "gnome-desktop-environment".

How can I force the removal of this package???  Thanks!

---

### Post by mikewhatever on 2009-11-17
I don't think you can remove sfwdec-gnome and keep the other packages, because the latter depend on the former. However, I am not seeing why you want gnome and gnome-desktop-environment installed. They are not part of the default Ubuntu installation, and must have been pulled in with other packages you installed later. Anyway, all three are safe to remove.

---

### Post by hysbyswr on 2009-11-17
Thanks!

I had just assumed that I had needed those other packages for Gnome to work...

Anyway, I removed them and everything is working fine...

---

