---
title: "Progressive xorg font corruption, Radeon 7000"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yelvington on 2009-03-29
I upgraded an IBM ThinkCentre to Jaunty Jackalope without incident, so naturally I went looking for trouble by pulling a Radeon 7000 card from a PC I hadn't used in a long while and putting it in the ThinkCentre, in hopes of getting better video performance. 

Now I have a problem: Fonts seem to get corrupted, with letterforms gaining and losing pixels, mostly at the top and bottom. Switching system fonts didn't make the problem go away. Switching off font smoothing (in the preferences -> appearances tool) helped somewhat, in that I can actually read the screen again, but the problem is still here.

I'm not sure if this is a software bug that should be reported, or a config problem, I hadn't used the card for awhile, but it was fine under an older version of Ubuntu, probably Feisty, on the old PC.

To compound the problem, I am unable to revert to the built-in Intel 865G graphics, as the X startup now fails with "failed to pin back buffer / cannot allocate memory" error. There's nothing informative in xorg.conf, so I can't figure out why pulling the Radeon card doesn't put me right back where I came from.

---

### Post by jerrylamos on 2009-04-14
The same gradual font degradation on Jaunty happens on my IBM Thinkpad R31, which is 1.0 gHz Intel Celeron, integrated Intel i830 graphics.  Up thru about Alpha 5 it was O.K. but something since, even in Beta, has changed.  I don't have a library of Alpha levels to check.

It's dual booted with Intrepid which has no such problem, so I don't think it is the hardware.

I'm trying to figure out how to define a Launchpad bug for this.

Jerry

---

