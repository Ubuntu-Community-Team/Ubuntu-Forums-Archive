---
title: "Current state of openoffice-3.x (Will sponsor/contribute personally)"
date: 2008-07-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by curtis on 2008-07-23
Hello,
I am happy to personally help with getting openoffice-3.x in to the 8.10 final release. What is the current state of it?

I would look around - but too busy to be honest to see what is going on everywhere in the ubuntu community.

I am will be able to dedicate time my self on packaging/development work and possibly sponsor the work partially as an bounty but that is just that a possibility that money will be involved.

Thank you for reading this and I'll keep monitoring this thread,

Curtis

---

### Post by syxbit on 2008-07-23
checking the official OOo site for info shows that their goal of releasing beta2 the 1st of July hasn't happened, so they're behind schedule, which means that it's unlikely (unless something changes) to ship in intrepid.
unfortunate, yes. which is why i switched to Arch. No more freezes making me miss software for another 6 months.
i hope it makes it, but it's looking questionable right now.

[http://wiki.services.openoffice.org/wiki/OOoRelease30](http://wiki.services.openoffice.org/wiki/OOoRelease30)

---

### Post by Eclipse. on 2008-07-23
> **syxbit said:**
> checking the official OOo site for info shows that their goal of releasing beta2 the 1st of July hasn't happened, so they're behind schedule, which means that it's unlikely (unless something changes) to ship in intrepid.
unfortunate, yes. which is why i switched to Arch. No more freezes making me miss software for another 6 months.
i hope it makes it, but it's looking questionable right now.

[http://wiki.services.openoffice.org/wiki/OOoRelease30](http://wiki.services.openoffice.org/wiki/OOoRelease30)

Beta 2 is out there.

Hopefully it will make its way in, only time will tell I guess.

---

### Post by Foaming Draught on 2008-07-24
We got Firefox 3 beta in Hardy, so why not OO 3 beta in Intrepid?  (I expect that the stock answer is that Hardy is a LTS release).

I've had no problems with OO 3 yet.  The jury (of one, me) is out on its welcome splash.

---

### Post by klange on 2008-07-24
Well, they did destroy the dictionaries, but that's because the new extension-based dictionary system isn't done yet. (On Windows, disabling the extensions will fix the dictionaries, but I have yet to find a work around on Linux)

Other than that, OOo 3.0 in beta and beta 2 has been faster and significantly more stable than 2.4 ever was.

Also, PDF importer.

---

### Post by psyke83 on 2008-07-24
> **Foaming Draught said:**
> We got Firefox 3 beta in Hardy, so why not OO 3 beta in Intrepid?  (I expect that the stock answer is that Hardy is a LTS release).

I've had no problems with OO 3 yet.  The jury (of one, me) is out on its welcome splash.

You answered your own question in a sense when you referred to the stock answer.

Looking on the opposite side of the coin, what's wrong with OpenOffice 2.4.x? There's less incentive to include a beta release of a program that weights hundreds of megabytes in source and steals a lot of computing cycles from the build machines. As you said, Intrepid won't be a LTS release and thus the "cost/benefit ratio" is pretty low. If user testing reveals some serious regressions or unfinished features, then the developers will get harangued into a SRU after the final release of Intrepid.

Feel free to go ahead and "dedicate [your] time on packaging/development" - if you have a launchpad account, you can create a PPA and give it a shot yourself. Even if you build and package it perfectly, there's no guarantee it will get accepted into a non-LTS release (for the reasons outlined above).

---

