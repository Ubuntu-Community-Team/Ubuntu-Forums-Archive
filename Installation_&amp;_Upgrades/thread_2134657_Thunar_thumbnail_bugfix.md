---
title: "Thunar thumbnail bugfix"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by EAZ on 2013-04-11
Under Xubuntu, using XFCE with Thunar, there is a thumbnail-bug.


Ffmpegthumbnailer creates a thumbnail-cache folder under /.cache
Thunar does not uses /.cache but seraches its thumbs under /.thumbnails


The only thing you have to do is to create a link from /.cache/thumbnails as /.thumbnails

---

