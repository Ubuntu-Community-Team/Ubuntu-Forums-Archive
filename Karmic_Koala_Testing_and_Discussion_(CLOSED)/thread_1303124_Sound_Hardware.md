---
title: "Sound Hardware"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by picopir8 on 2009-10-27
I have several different hardware options listed in my sound preferences: Digital Out, Digital Out + Analog In, Digital Duplex, Analog Out, and Analog Duplex.

Presently I am using Analog Duplex because only that an Analog Out work.  I get no sound from the Digital options.

My question is, should I get sound when the digital options are selected?  They are listed so I assume my soundcard supports them, however, I guess they could be listed for everyone and we are supposed to know what our soundcards support.  Unfortunately I have no clue what my soundcard supports.  lspci reports that it is a:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by seeker5528 on 2009-10-28
It's possible that the port you have the analog speakers attached to could double as a digital output and is selectable in software or there is a separate output for digital.

It's also possible that it was cheaper to use a chipset that supports digital and leave the outputs for it off the motherboard, leaving you with digital options you can't actually use.

Any way you look at it, if you don't have digital speakers, and you have a digital/analog toggle, then when the digital stuff was enabled you would either get no sound at all or you would get something unpleasant (screeches, clicks, static, etc...).

Later, Seeker

---

