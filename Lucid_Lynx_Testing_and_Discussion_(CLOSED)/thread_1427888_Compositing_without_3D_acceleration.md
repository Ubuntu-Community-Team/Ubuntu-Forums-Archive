---
title: "Compositing without 3D acceleration"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by metallica1788 on 2010-03-12
The new theme introduces some transparancy,
but you need compositing to do that.
Maybe it is an good idea that we enable metacity compositing for people who use nouveau or another driver who doesnt support 3D.
This way everyone can have transparantie and nice shadows.
I already tested it in safe graphics mode and it works great.

---

### Post by psyke83 on 2010-03-12
Metacity compositing works with the VESA driver? That doesn't sound right.

On both of my systems, Metacity compositing is noticeably slower than Compiz (radeon 345M and intel 855gm integrated graphics).

---

### Post by metallica1788 on 2010-03-12
I got a warning that ubuntu could only use safe graphics,
and metacity compositing worked.
If it was just a bug we could still use it with nouveau.

---

### Post by cyberkilla on 2010-03-12
Metacity Compositing is very fast on my laptop. I use it with Nouveau and the nVidia binary driver just fine.

It's a shame it can't be configured a bit more though. The only issue I really have with it is that ALT+TAB - It is _slow_. If I could get ALT+TAB to use the app icons instead of thumbnails again, it might be less bothersome.

Then again, Metacity 2 is dead, according to one of the creators. It's all about Mutter (Metacity 3). I'm not sure I agree with this. Sounds like a foolish idea, considering that Mutter (supposedly) only supports 3D compositing.

What is the fallback? The old Metacity? Then you haven't really relieved yourself of the burden of it. It is silly that windows require GL to be displayed, when 99.99999% of their usage is actually 2D in nature.

Unless some fantastic new UI paradigm is invented which requires 3D, all they've done with Mutter & GNOME Shell is bump the hardware requirement. Stacking rectangles on top of each other can be done in 2D.

---

And the most common retort? "Well man, like, every piece of modern hardware has 3D support. Even my crazy new phone can crunch vertices." Yes, that's very true, except the hardware support just isn't reliable enough to make a sweeping generalisation like that.

---

