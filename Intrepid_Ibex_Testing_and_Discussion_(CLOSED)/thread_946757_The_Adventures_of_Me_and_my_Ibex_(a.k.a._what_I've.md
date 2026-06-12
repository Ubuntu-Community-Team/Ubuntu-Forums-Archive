---
title: "The Adventures of Me and my Ibex (a.k.a. what I've found so far)"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DeepThoughts on 2008-10-13
I've been running the Ibex for a couple of weeks and although it works really well for the most part I've found some extremely annoying bugs.

**#1. Banshee doesn't work**
Well, that sorta depends on how you define work. It will play music but it crashes when changing songs. This would be bug [#279800]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/279800") on launchpad

**#2. Booting will sometimes halt and the computer will beep extremely loud**
Most of the time the boot process works fine (and much quicker than the Heron) but sometimes it goes completely bananas and just beeps extremely loud. Turn off the computer and the start it again and it will boot just fine. [#279187]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187") and [#235662]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662") seems to cover this

**#3. Redraw issues with compiz**
Compiz works fine for a while then completely craps out. It stops redrawing the contents of the applications. I've attached two screenshots which shows this issue. Nothing I do, except turning off Compiz, can get it to start drawing again. I have a nVidia card and read somewhere that turning Force Full GPU Scaling in nVidia Settings -> GPU 0 -> DFP 0 off and then on was a workaround for a similar issue. This isn't the case for me, it is true that turning it off and then on will give you the contents of the window but it will still not redraw, whick means that you i.e. can't type or scroll. Metacity with compositing turned on does not have this issue. (I'm also unsure if this affects all programs or only pure GTK+ ones)

I've searched launchpad for this bug but can't find it. Does anyone know if it exists or if I should start one? The compiz bug is by far the most annoying one.

---

