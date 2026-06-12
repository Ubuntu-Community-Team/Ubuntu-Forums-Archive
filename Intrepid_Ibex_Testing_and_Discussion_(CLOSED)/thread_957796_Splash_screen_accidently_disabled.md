---
title: "Splash screen accidently disabled?"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by heavensblade23 on 2008-10-24
I get the bar that goes back and forth, but as soon as it gets to the part where it's a progress bar, instead I get a bunch of system messages before it eventually prompts me for a password.

I'm not sure whether this happened with a recent update, or because I had to mess around with some system settings recently (changing the kernel scheduler, changing my swap and home to be on encrypted partitions).  At one point I had both the progress bar and my home directory working together...it would pause halfway through, ask for the password to my home partition, and then continue.  That's what I want it to do again, but I don't know how.

---

### Post by heavensblade23 on 2008-10-26
It's a bug.

Solution was to change swap to use a passphrase instead of grabbing a random one from /dev/random, and following the instructions in the bug repor.

---

