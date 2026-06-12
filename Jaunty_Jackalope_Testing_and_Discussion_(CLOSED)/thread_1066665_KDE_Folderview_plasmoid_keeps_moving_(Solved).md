---
title: "KDE Folderview plasmoid keeps moving (Solved)"
date: 2009-02-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RIchard James13 on 2009-02-11
I am trying to use activities in KDE but when I place multiple folder view widgets on the desktop they keep jumping around after I place them.

Most of the time they jump to the top left but at other times they seem to jump to the centre.

For instance the placement

[[img]http://www.postimage.org/aV1HFiUi.jpg[/img]](http://www.postimage.org/image.php?v=aV1HFiUi)

Stays fine until I move the mouse off of the folderview widget and turns into this.
[[img]http://www.postimage.org/aV1HFUjr.jpg[/img]](http://www.postimage.org/image.php?v=aV1HFUjr)

After much searching the Internet I came across the following post.

[http://forum.kde.org/-solved-plasmoid-placement-sit-stay-t-31040.html]("http://forum.kde.org/-solved-plasmoid-placement-sit-stay-t-31040.html")

On Kubuntu Jaunty you just run
kquitapp plasma; rm ~/.kde/share/config/plasma-appletsrc; plasma

It removes all you plasma settings and resets it to default.

---

