---
title: "Re: Lucid Alpha 1 released"
date: 2009-12-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tjapko on 2009-12-13
Up to kernel 2.6.32-4 Lucid Lynx works fine. When I upgrade to kernel 2.6.32-7 the system starts only in low resolution. 
If I install from the latest CD I also get only low resolution. If I reinstall with the earlier CD everything is fine.

None of the suggestions that I find on the Xorg site works. 

Any ideas on avoiding this breakdown?

N.B. On a different disk Karmic Koala runs without problems as well.

---

### Post by Elfy on 2009-12-17
moved from the fridge

---

### Post by cariboo on 2009-12-17
There are several threads on this problem in this sub-forum, depending on what graphics adapter you are using, you will have to either put up with it, or install the latest drivers from the manufacturer.

---

### Post by jerrylamos on 2009-12-18
The -8 kernel runs well on my IBM tower with i845 video.  The -7 hung up either on initial gdm display or shortly thereafter.

I booted the -5 kernel and then did sudo aptitude update, sudo aptitude full-upgrade which installed the -8 kernel which is running well (for an Alpha).

If all you've got is a -7 kernel, then try booting in recovery mode, select root prompt, do dhclient, exit, then repair broken packages or whatever it's called.

Since intrepid 8.10 I've had periods of even months where one or another of my test pc's would boot to black screen which were eventually fixed as a result of a flurry of launchpad bugs & helpful posts.

Jerry

---

