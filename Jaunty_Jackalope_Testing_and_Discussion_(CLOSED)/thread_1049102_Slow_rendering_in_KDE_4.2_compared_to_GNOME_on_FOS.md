---
title: "Slow rendering in KDE 4.2 compared to GNOME on FOSS ATI drivers..."
date: 2009-01-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2009-01-24
I've noticed that KDE 4.2 is a lot slower at rendering than GNOME, and I assume this is due to KWin - is it possible to run compiz with KDE's normal window borders, rather than with emerald taking over?

---

### Post by xerosis on 2009-01-24
I'd heavily suggest it's the new X rather than KDE's compositing as it's always been better than gnome for me. (I can't even get any compositing with the new X)

---

### Post by Mazza558 on 2009-01-24
It was like this when I used KDE Neon in Intrepid.

---

### Post by inportb on 2009-01-24
How slow is slow?

---

### Post by Mazza558 on 2009-01-24
> **inportb said:**
> How slow is slow?

When you scroll down it takes about 200ms for the previous bit of page to move upwards for the next bit of page to appear. There's also artefacts(e.g purple/green lines) sometimes when opening menus. When windows are un-minimised, the zoom animation blacks out the window until it's fullsize, creating a flashing effect.

---

### Post by gmclachl on 2009-01-24
I can't talk about KDE4 other than the fact I use it at home with a nvidia card and it works well. 

My machine at work has an ATI card and with the foss drivers it is unusable, redrawing is painfully slow.

---

### Post by Progressive on 2009-01-24
This is a known issue. It is because KDE uses bits that currently cannot be accelerated.

[http://www.phoronix.com/forums/showthread.php?t=14903](http://www.phoronix.com/forums/showthread.php?t=14903)

This requires upgrades in EXA itself before the driver can implement it.

Of course, using XAA it should be possible to run with full acceleration... but not as fast as possible with EXA obviously.

---

### Post by Mazza558 on 2009-01-24
Thanks, so does this mean changing to compiz won't make a difference?

---

### Post by inportb on 2009-01-25
Darn. Well, I've been getting acceptable performance; it could be better =p

---

### Post by Progressive on 2009-01-25
Switching to compiz should make no difference since the problem is that the open source ATI driver cannot accelerate certain aspects of KDE4.

You can switch to XAA, switch to Catalyst, or switch to KDE3 or Gnome.

I personally experience no major KDE4 problems with EXA on my R500, but that might be because my CPU is more powerful.

---

### Post by _tom_ on 2009-01-25
Having the same problem on Jaunty with kde 4.2 but not with Intrepid (also kde 4.2). Both ubuntu systems are installed on the same computer (HP nx7400, intel graphics).

p.s. I know glxgears is no benchmark but it's strange that I get around 950 fps with intrepid and only 35 fps with jaunty (dri is reported to be used).

---

### Post by SunnyRabbiera on 2009-01-25
Well understand that kde4.2 is still pre release, I see it has this odd fullscreen issue that I hope is fixed for the full release.

---

### Post by forcecore on 2009-01-25
half offtopic but i have nvidia 8200 on 8.10 with 180.22 and 2D is soo slow, i can understand 3D BUT 2D, i really hope that kde 4.2 with 9.04 casual desktop is fast (i do not like effects and kde 4.2 is good looking in 2D)

---

### Post by RAOF on 2009-01-25
> **forcecore said:**
> half offtopic but i have nvidia 8200 on 8.10 with 180.22 and 2D is soo slow, i can understand 3D BUT 2D, i really hope that kde 4.2 with 9.04 casual desktop is fast (i do not like effects and kde 4.2 is good looking in 2D)

The binary nvidia driver's 2D performance just isn't terribly good.  This can be annoying, as you've found :/.

You could *try* nouveau, which has excellent 2d performance for me.  Your mileage *will* vary, though; your nv5x series chip isn't nearly as well supported as my nv4x.  You'll need to enable XRender compositing in kwin before nouveau will do acceleration for you, too.

Other downsides of nouveau: no suspend/resume support, and no 3d.

**EDIT:** Yup, nouveau for the win.  Nice and fast.  Now, if only I could convince KWin that it should be able to act as an XRender-backed compositing manager...

---

### Post by Mazza558 on 2009-01-27
I've tried KDE 4.2 with XAA and it's exactly the same. 

Shame, because otherwise KDE4'd be usable.

---

