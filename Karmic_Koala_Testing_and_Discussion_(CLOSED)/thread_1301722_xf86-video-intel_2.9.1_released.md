---
title: "xf86-video-intel 2.9.1 released"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-10-26
[xf86-video-intel 2.9.1 Provides More Fixes](http://www.phoronix.com/scan.php?page=news_item&px=NzY0MQ)

Will it make it in? :(

3 bugfixes
> Complete list of fixes in 2.9.1 compared to 2.9.0
-------------------------------------------------
 * Fix corruption and artifacts due to wrong colors in the colormap
   with X server 1.7

 * Fix incorrect rendering, such as missing scrollbar arrows in some
   themes ([http://bugs.freedesktop.org/show_bug.cgi?id=24459](http://bugs.freedesktop.org/show_bug.cgi?id=24459))

 * Fix black screen when X server is reset
   ([https://bugs.freedesktop.org/show_bug.cgi?id=24383](https://bugs.freedesktop.org/show_bug.cgi?id=24383))

 * Fix regressions detecting DVI monitors

   [http://bugs.freedesktop.org/show_bug.cgi?id=24255](http://bugs.freedesktop.org/show_bug.cgi?id=24255)
   [http://bugs.freedesktop.org/show_bug.cgi?id=24282](http://bugs.freedesktop.org/show_bug.cgi?id=24282)
   [http://bugs.freedesktop.org/show_bug.cgi?id=24458](http://bugs.freedesktop.org/show_bug.cgi?id=24458)

It looks like one of the fixes was already [incorporated into ubuntu](http://changelogs.ubuntu.com/changelogs/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.9.0-1ubuntu2/changelog).

Why not take the other two? :P

---

### Post by benjamimgois on 2009-10-26
I think that drivers should always be updated. No matter the distribution cycle.....

---

### Post by slakkie on 2009-10-26
> **benjamimgois said:**
> I think that drivers should always be updated. No matter the distribution cycle.....

Why? You know why people need to test during development. Things could break, you don't want that to happen in a stable release.

---

### Post by benjamimgois on 2009-10-26
> **slakkie said:**
> Why? You know why people need to test during development. Things could break, you don't want that to happen in a stable release.

Well, i assume that if the driver was released as "stable" it means that the developer already test it.

---

### Post by andrewabc on 2009-10-26
> **benjamimgois said:**
> Well, i assume that if the driver was released as "stable" it means that the developer already test it.

But it might not work with other drivers or part of the OS. That's why ubuntu doesn't just slap in any new drivers or anything after a release.
Sometimes new drivers would be great, and sadly you have to wait 6 months for the new ubuntu version to fix it. An example would be intel drivers for jaunty that sucked (worse than intrepid), have now been fixed for karmic.

---

### Post by psyke83 on 2009-10-26
> **benjamimgois said:**
> Well, i assume that if the driver was released as "stable" it means that the developer already test it.

"Some" developers tested, only against their machines. The Ubuntu user-base is much wider, and there are probably going to be regressions that the developers miss - otherwise, what's the point of user bug reports?

Also, Xorg driver updates sometimes require Xorg stack and/or kernel updates to function properly. You can't expect a stable release to do this.

There's a chance you'll see the new Intel driver in the [X-Updates PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates").

---

### Post by flipper9 on 2009-10-26
With the latest updates to x-swat and x-org-edgers, they break Intel setups on Eee Laptops.  I'm going to stick with the stock drivers for now.  When I update to the updated ones, they keep you from logging into Gnome due to issues with the Mesa software and Compiz.

---

