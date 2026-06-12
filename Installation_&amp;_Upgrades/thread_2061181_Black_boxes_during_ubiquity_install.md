---
title: "Black boxes during ubiquity install"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by valtam on 2012-09-21
Hi all,

I'm doing a remastersys of Ubuntu 12.04. I started out with the Ubuntu mini cd and built from there. It is nearly complete however, at the start of the install wizard, from the first dialogue box, through to the last just before the slideshow starts, they look like this:

[IMG]http://i.imgur.com/tWE9j.png[/IMG]

[IMG]http://i.imgur.com/mlPro.png[/IMG]

The slideshow after that looks fine. The only information I can find so far is that is **may** be related to gtk. Any ideas? Thank you :)

---

### Post by valtam on 2012-09-21
Fixed it, added:

gnome themes standard
gnome accessibility themes
gtk2-engines
gtk3-engines-unico

then selected a dual gtk2/gtk3 theme in Appearance.

---

