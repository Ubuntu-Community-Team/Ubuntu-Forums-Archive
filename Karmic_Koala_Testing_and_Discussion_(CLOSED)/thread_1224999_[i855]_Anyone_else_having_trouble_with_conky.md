---
title: "[i855] Anyone else having trouble with conky?"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kareeser on 2009-07-28
[Intel 82852/855GM Onboard video]

Since updating to Karmic, conky's been acting weird, and not staying put in the background.

I use [this setup](http://gnome-look.org/content/show.php/CONKY-colors?content=92328), so it should, by default, stay in the background at all times, and be transparent.

However, after an undetermined period of time, the background will just switch to grey.

In one instance, conky spontaneously stopped staying behind open windows, and became "always on top". Weird.

Anyone else experience this?

---

### Post by marginean.m on 2009-07-30
yep! me too!
 It works if I use "own_window yes" + "own_windows_transparent no" in witch case the transparency is gone..:( 
Or you could set the "own_window_type normal" instead of "override" and keep the transparency but in this case when you click the "SHOW DESKTOP" button conky will be minimized too. This is kinda annoying for me...
I would really appreciate a piece of advice here! Thanks!

---

### Post by magisterludi on 2009-07-30
Same problem, the bug is already known:
[https://bugs.launchpad.net/ubuntu/+source/conky/+bug/405340](https://bugs.launchpad.net/ubuntu/+source/conky/+bug/405340)

---

### Post by tekstr1der on 2009-07-30
Yes, I can force this to happen by rotating the compiz cube. Apparenty related to gtk updates mentioned in the bug report.

---

### Post by Vanishing on 2009-07-30
Strange....my conky seem to work like before, rotating the cube will not turn it grey..o.o..maybe its grey already?:D

---

### Post by ace214 on 2009-08-03
Bumping to see if anyone has fixed the issue of Conky always being on top of other windows...

---

