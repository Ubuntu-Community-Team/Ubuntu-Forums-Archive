---
title: "Intel graphics: Change in output names"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by penguin42 on 2009-06-28
Hi,
  Just a note to any one with custom Xorg.conf on Intel i945 or similar;
it looks like the output names have changed in a recent Karmic update.

My outputs used to be LVDS and VGA but are now LVDS1 and VGA1.

If you have an xorg.conf line of the form:

  Option "monitor-LVDS" "moninternal"

then you will have to change it to match the new names.  I found the names by doing xrandr.

(I have an xorg.conf because my external monitor doesn't get it's frequency/res detected).

Dave

---

### Post by psyke83 on 2009-06-28
> **penguin42 said:**
> Hi,
  Just a note to any one with custom Xorg.conf on Intel i945 or similar;
it looks like the output names have changed in a recent Karmic update.

My outputs used to be LVDS and VGA but are now LVDS1 and VGA1.

If you have an xorg.conf line of the form:

  Option "monitor-LVDS" "moninternal"

then you will have to change it to match the new names.  I found the names by doing xrandr.

(I have an xorg.conf because my external monitor doesn't get it's frequency/res detected).

Dave

Maybe you could consider filing a bug on your issue so that the driver will have better autodetection of your monitor?

---

