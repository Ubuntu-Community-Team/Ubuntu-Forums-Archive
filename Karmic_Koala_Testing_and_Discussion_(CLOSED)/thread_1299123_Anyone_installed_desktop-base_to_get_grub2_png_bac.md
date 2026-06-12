---
title: "Anyone installed desktop-base to get grub2 png backgrounds?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-10-23
The pngs get stored in /usr/share/images/desktop-base

You get all these but how do you change what is displayed?


**Damn must have missed the theming thread when my machine was busted.**

---

### Post by philinux on 2009-10-23
Found this new file.

/etc/grub.d/05_debian_theme

So part of this reads..
```
# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,**/usr/share/images/desktop-base}/nightly-wallpaper**.{png,tga} ; do
```

So editing the png name here then sudo update-grub should get you a new grub2 background. But I chose the wrong file and it screwed up the grub resolution.

Resolution needs to be 640x480 I think.

---

### Post by ranch hand on 2009-10-23
05_debian-theme is set to get them from /usr/share/images/grub.  I create that file and put my images there.  I use the same image for the menu, xspalsh and GDM (uses /usr/share/images/xsplas/bg_2560x1600 for its image).  Get the all the sizes right and it is seamless.

The menu theme images are 640x424 @ 72,000p/in if you use theirs.  If you use yours you may want to tweek that a bit to match all the way through.

---

