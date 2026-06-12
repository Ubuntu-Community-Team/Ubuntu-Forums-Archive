---
title: "screensaver heats up GPU"
date: 2008-09-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-09-30
the screensaver is now working , atleast it activates, but it is driving my GPU temp up by 15>20 C .

---

### Post by DavidONE on 2008-09-30
I noticed a while back that some screensavers use 100% CPU. If you run 'top' while previewing your screensaver, you can see if that's the problem and select another.

---

### Post by ronacc on 2008-09-30
its not my CPU ( amd64x2 4600) thats heating up its my GPU (nvidia 7600 gs) . I'll try a few different ones and see if its all of then or just some .

---

### Post by ssam on 2008-09-30
all screen savers use more power than just letting the machine be idle. there is no good reason not to set the screensaver to blank screen.

---

### Post by ronacc on 2008-09-30
I agree that doing "something" (any screensaver) uses more power than doing "nothing" (no screensaver) I was just rather alarmed by the spike in GPU temp ,that is not something I see on this box under normal use . It definately is not all screensavers that do it for instance cosmos which is basicly just a slide show shows no increase in gpu or cpu temp , euphoria which generates a constantly moving/changing pattern shows a big jump in gpu and a small increase in cpu , galaxy which does generate a shifting pattern but less agressively shows no cpu jump but a small gpu increase but cannot be recovered from by moving the mouse, you have to hit a key to get back to desktop ,hypertorus does not activate at all, the only conclusion I can come to is that the whole thing is flaky/inconsistant .

---

### Post by ronacc on 2008-09-30
update , checked my hardy install on the same box , gpu heats up with some ss's there too , guess I hadn't noticed it before because I just hadn't used one of the screensavers that does it .

---

### Post by pressureman on 2008-09-30
Considering that some OpenGL screensavers are bordering on the same complexity as FPS games, it's not surprising that the GPU heats up. And the non-OpenGL screensavers, which make the CPU do all the work, obviously heat up the CPU. Quite a few of the default screensavers shipped with Ubuntu drive the CPU to 70% or more on my laptop. Some of them are ridiculously CPU-intensive.

As ssam says, a blank screen is as good a screensaver as any. LCD panels especially, have little to no need whatsoever for a screensaver, as there isn't a stream of electrons hitting a phosphor coating - LCD panels don't get "phosphor burn-in".

On the other hand, it's nice to have some kind of visual feedback that the computer is in screensaver mode, and hasn't died or black-screened.

---

### Post by ronacc on 2008-09-30
I realise that screensavers are unneeded on lcd's and I just use one to remind me to turn the things off before I leave for long periods or hit the sack for the night , and I generaly use cosmos as a screensaver which as I said above is basicly a slideshow and puts essentialy no load on either the cpu or gpu .I was just playing around with different ss's trying to find one that would actualy activate since the ss has been broken for most of intrepid .

---

