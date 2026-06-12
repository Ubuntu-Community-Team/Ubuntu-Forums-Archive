---
title: "How do I upgrade Karmic from pre alpha to alpha 1"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flipmatthew on 2009-05-14
How do I upgrade from Karmic pre alpha to alpha 1? ( without downloading iso directly )

---

### Post by super.rad on 2009-05-14
You just make sure you have all updates installed (if you don't know this then you probably shouldn't be using alpha software)

---

### Post by jerrylamos on 2009-05-14
I've got them both installed on a triple boot pc.  I haven't seen any difference for example gtkperf runs about 32.4 on both of them, with linux-image 2.6.30-5 on both.  It came via update on the boot built from changing sources.list from jaunty to karmic, and came with the alpha 1 alternate install disk.

I have two of them just in case we get an update like the recent one where hal blew a number of us out of the water.

Jerry

---

### Post by Starks on 2009-05-14
if you use the update manager normally and have all the latest packages, you have alpha 1.

---

### Post by cecilpierce on 2009-05-14
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by taavikko on 2009-05-15
> **jerrylamos said:**
> I've got them both installed on a triple boot pc.  I haven't seen any difference for example gtkperf runs about 32.4 on both of them, with linux-image 2.6.30-5 on both.


Alpha{1-6} is nothing more than a snapshot of repositories.
Release may contain some targeted bug fixes, but it isn't a magical release to fix bugs.


If your sources.list point to karmic, then that's what you get when doing upgrades. This isn't debian with {stable,unstable,experimental}.

someone should really write a "sticky" about upgrading, for all newcomers and for those who doesn't quite yet crasp how system works.

For super.rad's comment, +1

---

### Post by 23meg on 2009-05-15
[QUOTE=taavikko]someone should really write a "sticky" about upgrading, for all newcomers and for those who doesn't quite yet crasp how system works.[/QUOTE]

It's in the works.

---

### Post by taavikko on 2009-05-15
> **23meg said:**
> It's in the works.

Great, thanks (pronounced with a thick Scottish accent)

---

### Post by Krause on 2009-05-15
> **super.rad said:**
> You just make sure you have all updates installed (if you don't know this then you probably shouldn't be using alpha software)

Well thats not really fair, in past Debian releases you could change the repository to a higher version and do the updates, but the distribution wasnt fully updated until you ran a apt-get dist-upgrade. He was probably just over complicating it.

---

### Post by davideotape on 2009-05-15
> **23meg said:**
> It's in the works.


Glad to hear it :D I remember asking this question myself during the jaunty dev cycle, and I was pointed to plenty of duplicate posts :p

---

### Post by Gina on 2009-05-15
Good point - one that I have overlooked on my Ubuntu HowTo website.  I'll add that to my list of updates - I'm half-way through updating to cover 9.04.

---

