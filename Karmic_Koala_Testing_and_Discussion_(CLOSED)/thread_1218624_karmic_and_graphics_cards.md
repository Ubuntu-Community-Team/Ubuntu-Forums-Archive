---
title: "karmic and graphics cards"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wcutrombonekid on 2009-07-20
does anyone know if karmic koala is going to still have the intel graphics cards blacklisted???

i would really like to play some games on ubuntu because they perform so much better, but i can't because of my graphics card.

---

### Post by QIII on 2009-07-20
They are working on Intel graphics support.

I think UXA support is available in the current alpha.

I'm sure they'd appreciate it if you would help with testing and give them some feedback.

---

### Post by wcutrombonekid on 2009-07-20
i would, but i really don't know enough about linux to do that.  I know enough for day to day use and to find out anything i need, but i really don't think i have enough to test

---

### Post by QIII on 2009-07-21
All it takes to test Karmic is to install it, set up a Launchpad account and try to use Karmic as you would use Jaunty.

If you have a problem, you can report it by giving feedback with as much information as you possibly can.  You don't need to be technically minded.  You just need to report the behavior you are seeing and why you think it is amiss.

It is best, of course, to give as much detail as you can about errors encountered and shown on your screen, all the details you can muster about the specifications of your machine, etc.

There are those who get into very technical areas, of course.  But you needn't be one of them to help the community effort.

In your case, you may simply find that the current Alpha gives you fits with regard to your graphics chipset.  That is important for the developers to know.

---

### Post by ghindo on 2009-07-21
> **QIII said:**
> They are working on Intel graphics support.

I think UXA support is available in the current alpha.

I'm sure they'd appreciate it if you would help with testing and give them some feedback.UXA has been the _only_ option for Intel graphics for a while, now.  It's been working fine for me. :popcorn:

---

### Post by QIII on 2009-07-21
As I am sure you are aware, UXA is not the default.  You had to make modifications.

This is from a June update:

**> New Intel video driver architecture available for testing**
 In later Karmic milestones the Intel video driver will most probably switch from the current “EXA” acceleration method to the new “UXA”. This will solve major performance problems of Ubuntu 9.04, but is still not as stable as EXA, which is why it is not yet enabled by default. We invite you to help testing UXA, please see the instructions and feedback page.

---

### Post by ghindo on 2009-07-21
From [a post on the ubuntu-devel mailing list]("https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028286.html"):> The 2.7.99.1 -intel driver has been uploaded to Karmic today.

This version switches us to the UXA acceleration mode.  In fact,
upstream stripped out EXA acceleration altogether, so it's UXA or bust
now.

---

### Post by QIII on 2009-07-21
Again:  Karmic, which is what the OP asked about.  I answered that it was in the current Alpha.

To use it in Jaunty, one has to make changes.  I regret that I didn't look at your distro and missed that you are using Karmic.

Not trying to start a p*ssing match.

I suggested that the OP get involved in testing Karmic, since he seems to be having an issue in Jaunty that should be dealt with in Karmic.

---

### Post by ghindo on 2009-07-21
Sorry, not trying to start an argument.  I'm running on little sleep and probably misunderstand posts in this thread.

I'll post when I have a bit more coherency.

---

### Post by jerrylamos on 2009-07-21
> **ghindo said:**
> UXA has been the _only_ option for Intel graphics for a while, now.  It's been working fine for me. :popcorn:

Well, on intel i830 and i845 uxa and KMS work for me, however on the i830 video performance as measured by GtkPerf from Synaptic is nearly 2x slower than Intrepid.  On i845 it's about 37% slower than vesa.

Get that, the "accelerated uxa" code is slower than ancient vesa!  There's some launchpad bugs including #382017.

Seems to me, for GtkPerf anyway, ditch "uxa" and just use vesa.  That's what I do.  Karmic feels definitely crisper that way.

Jerry

---

### Post by QIII on 2009-07-21
Fortunately for me, I don't have any Intel graphics on any of my machines...

I've been testing nVidia and AMD/ATI performance, which seems good on ATI with Catalyst and poor on an old nVidia card (it's old enough that it is not supported by nVidia any longer.  The open source driver doesn't work for 3D.)

---

### Post by psyke83 on 2009-07-22
> **jerrylamos said:**
> Well, on intel i830 and i845 uxa and KMS work for me, however on the i830 video performance as measured by GtkPerf from Synaptic is nearly 2x slower than Intrepid.  On i845 it's about 37% slower than vesa.

Get that, the "accelerated uxa" code is slower than ancient vesa!  There's some launchpad bugs including #382017.

Seems to me, for GtkPerf anyway, ditch "uxa" and just use vesa.  That's what I do.  Karmic feels definitely crisper that way.

Jerry

Just keep in mind that some users also notice drastic improvements (in 2D and 3D rendering) with UXA/DRI2. It depends on your particular chipset and whether there are any unresolved performance regressions (as is the case with mine since the 2.6.31-rc1 kernel).

---

### Post by psyke83 on 2009-07-22
> **wcutrombonekid said:**
> does anyone know if karmic koala is going to still have the intel graphics cards blacklisted???

i would really like to play some games on ubuntu because they perform so much better, but i can't because of my graphics card.

The intel 2.8.0 driver and mesa 7.5 were uploaded yesterday. I recommend you wait for alpha 3 (or grab tomorrow's daily live cd), and do some testing before installing Karmic.

Depending on your intel chipset, performance is hit and miss (mostly hit, as most of the regressions have been resolved). I suspect by alpha4/beta, Intel graphics performance will be much improved across the board for everybody (IMHO).

If you're still running Jaunty, you could consider testing out the instructions in my guide.

---

### Post by nanog on 2009-07-22
I'm using 2.6.30 rt and the edgers xorg/xserv (in karmic and jaunty). I am  getting flawless no-tear HD output on intel 945.

---

### Post by wcutrombonekid on 2009-07-24
i think my graphics card is an intel X3100

---

