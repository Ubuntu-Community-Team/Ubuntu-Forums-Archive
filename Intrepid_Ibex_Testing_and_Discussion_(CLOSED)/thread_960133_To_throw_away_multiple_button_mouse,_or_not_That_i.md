---
title: "To throw away multiple button mouse, or not? That is the question."
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PierreDeKat on 2008-10-27
Well, apparently [Intrepid has a whole new way of dealing with input devices]("https://wiki.ubuntu.com/X/Config#Input%20Configuration%20with%20HAL"), including mice, to the extent that Btnx no longer works.

Suddenly those extra buttons on my mouse are about as useful as teats on a boar hog.

This is particularly true in light of the fact that there's about zero documentation on how to set up an fdi file in your /etc/hal/fdi/policy directory to configure an input device the way you want it.

Judging by the way that this change has caught a lot of us with "unusual" mice flat-footed, [including the developer of btnx]("http://www.ollisalonen.com/btnx/"), I would have to assume that supporting such mice is a fairly low priority for Ubuntu developers in general.

So I would like to pose the question: should I throw out my unusual mouse and go back to straight left-click, right-click, and scroll?

Or should I keep my old mouse around for sentimental value?

---

### Post by sloggerkhan on 2008-10-27
Or should you go to launchpad and wherever else and bitch about how there's still no decent gui to configure input devices?

That's what I'd do. There ought to be a way you could go to a CP and just set all the buttons of whatever input device you have to do what you like.

---

### Post by MaX on 2008-10-27
I surely hope that this fdi thing supports all kinds of inputs, Analogue joysticks, throttles, buttons, top-hats, scroll wheels etc.

That way we might once and for all get something like Microsofts DirectInput which works surprisingly well.

---

### Post by Yashiro on 2008-10-27
Just don't upgrade till it's all sorted out and documented to a resonable level.

---

### Post by ajgreeny on 2008-10-27
Just for your information, I have been using a **Trust Ami Mouse - Dual Scroll** with two side buttons, for the last 4 years and I did miss the facility for the side buttons to do Back and Forward in firefox, as they did in WinXP, which had never happened in Ubuntu until recently.  Whether this was the move to Hardy or the fact that it is now FFv3, I don't know but I found by accident a few days ago that the side buttons now work as they did.  Hooray!

---

### Post by forumache on 2008-10-27
It works out of the box for me (kind of).
I have a mouse with 10 buttons (left, right, middle, scroll up, scroll down, scroll left, scroll right, forward, backward, extra button).

I had to remap some buttons using .xmodmaprc file.

First test if your mouse buttons work:
run xev in a console, then focus on its window, start clicking buttons, see how they are detected.

If all are detected, you are lucky, just need to remap them if they don't do what you want.

Of course, you may not reach the usability you had before with btnx, but I'm pretty happy with my 10 buttons mouse.

---

### Post by tonyric on 2008-10-27
My Logitech Nano has all of the buttons configured OOB with 8.10. That said, I need to change the buttons around so I have back/forward in the right place.

---

