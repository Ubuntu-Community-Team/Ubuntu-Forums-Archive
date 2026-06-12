---
title: "system crash on kernel 2.6.27-7"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by nittanylion on 2008-10-24
Just updated to a new kernel today, and I'm getting repeated crashes anytime I try to use that kernel. I'm typing this using 2.6.24-19 (i just picked it out of several, and it happened to work). Whenever I started up the system using 2.6.27-7, the system would completely halt within a few minutes of starting up, and the Caps Lock & Num Lock LED lights would continuously blink. Everything is frozen (mouse included), and I have to hold in the power button on the laptop to get it to shut down. 

This actually has happened in prior versions, just not nearly as frequently - I think it happened twice that I can remember since I've upgraded to Ibex. Something happened today that severely increased the frequency.

Any ideas how I can troubleshoot this, considering the system totally and completely freezes? I tried using the "Safe Mode", where it drops to a root shell, and I'll launch an Xserver through that -- however, that was unworkable. xorg.0.log does have 1 error: "Intel(0) underrun on pipe B", but I don't know if that's related.

---

### Post by nittanylion on 2008-10-28
bumping because it's still happening

---

### Post by dabl on 2008-10-28
I'd start with the basics and run memtest overnight.

---

### Post by sdowney717 on 2008-10-28
perhaps you could try reinstalling the kernel use synaptic to remove and then reinstall.

---

### Post by nittanylion on 2008-10-29
Thanks for the replies! 

Memory test passed with no errors. Reinstalled the kernel, as suggested.

So far, I have been unable to reproduce this error. That being said, Murphy's Law is definitely in play for this one. It only happen when I'm sitting in class (You know, at the point where it screws me the most):

Friday - Completely unusable in the 2.6.27-7 kernel after multiple restarts.
Sat/Sun/Mon - no problems
Tuesday - Completely unusable in the 2.6.27-7 kernel

Again, this happens within a few minutes / second after logging in ONLY using the 2.6.27-7 kernel. I've tried reproducing the same conditions in class when I'm out of class, to no avail.

---

