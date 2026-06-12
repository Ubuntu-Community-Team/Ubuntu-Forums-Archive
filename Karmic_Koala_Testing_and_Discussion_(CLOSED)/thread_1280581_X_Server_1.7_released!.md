---
title: "X Server 1.7 released!"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-10-02
[http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ)

We still got almost a month, d'you think it's too late?

---

### Post by dinxter on 2009-10-02
> **froggyswamp said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ)

We still got almost a month, d'you think it's too late?
its way, way too late im afraid! :)

---

### Post by JanDM on 2009-10-02
Yes it's too late. X is too critical to update after feature freeze...

---

### Post by dinxter on 2009-10-02
1.7 was the plan, but sadly its taken a bit longer than predicted for its release

---

### Post by dinxter on 2009-10-02
see
[https://wiki.ubuntu.com/X/Roadmap/Karmic](https://wiki.ubuntu.com/X/Roadmap/Karmic)
particularly the section 
"UPDATE - As of Alpha-4, some components were unavailable"

---

### Post by chrisjsmith on 2009-10-02
Happy happy joy joy.  I HATE X with a passion.  Mainly thanks to ATI but that's another story.

---

### Post by MadsRH on 2009-10-02
> **dinxter said:**
> 1.7 was the plan, but sadly its taken a bit longer than predicted for its release

With the flow X has been released with, I'm sure this could have been predicted. But X is joining the 6 month cycle :-D, so hopfully we will never experience that again.

---

### Post by dino99 on 2009-10-02
> **froggyswamp said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ)

We still got almost a month, d'you think it's too late?

from Xorg:

"  == Mandatory XKB ==
The XKB code has seen a fair bit of cleanup and removal of code path
duplications. XKB cannot be disabled at compile-time anymore and the
presence of XKB data files is required at server startup. "

Curious: what about system without keyboard (hardware) ?

---

### Post by dino99 on 2009-10-02
> **froggyswamp said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ](http://www.phoronix.com/scan.php?page=news_item&px=NzU3OQ)

We still got almost a month, d'you think it's too late?

from xorg:  Requires libpciaccess and kernel 2.6.32.

---

### Post by zevans on 2009-10-02
> **dino99 said:**
> from xorg:  Requires libpciaccess and kernel 2.6.32.

For what? I've run 1.6.99 RCs, 1.7, and 1.8 on 2.6.31. Fact! Must be some extra goodness that depends on 2.6.32?

---

### Post by unimatrix on 2009-10-03
Sooo.. could someone make a PPA for X server 1.7?

---

### Post by 6205 on 2009-10-03
> **unimatrix said:**
> Sooo.. could someone make a PPA for X server 1.7?

who cares for 1.7? you will not notice difference.. same for newer kernel..

---

### Post by talkingwires on 2009-10-03
> **chrisjsmith said:**
> Happy happy joy joy.  I HATE X with a passion.  Mainly thanks to ATI but that's another story.How are you posting in this thread? From a terminal and Links? Your Windows partition? Carrier pigeon?

---

### Post by unimatrix on 2009-10-03
> **6205 said:**
> who cares for 1.7? you will not notice difference.. same for newer kernel..

I might be naive.
I'm still hoping that one day X will become fast and responsive.

---

### Post by froggyswamp on 2009-10-03
> **unimatrix said:**
> I might be naive.
I'm still hoping that one day X will become fast and responsive.
Looks like you're gonna move to Google OS and their "new window system" when released. Probably no company is concerned about speed as much as Google, kudos to them.

---

### Post by Slug71 on 2009-10-03
Well we could install the new kernel and X and start filing bugs now for 10.04. :P

---

### Post by dino99 on 2009-10-03
> **6205 said:**
> who cares for 1.7? you will not notice difference.. same for newer kernel..

Disagree, that's usefull for errors, freezes & breakages on intrepid nerds systems & so   :lolflag:

---

### Post by zevans on 2009-10-03
> **froggyswamp said:**
> Looks like you're gonna move to Google OS and their "new window system" when released. Probably no company is concerned about speed as much as Google, kudos to them.

Is that the one that seems strangely similar to BeOS? I thought Warp was pretty good too, pity that died...

Anyway - 1.7 works properly on my Intel chipset, 1.6 doesn't. How's that for noticing a difference?

---

### Post by VMC on 2009-10-03
> **zevans said:**
> Is that the one that seems strangely similar to BeOS? I thought Warp was pretty good too, pity that died...

Anyway - 1.7 works properly on my Intel chipset, 1.6 doesn't. How's that for noticing a difference?

What Intel chipset do you have. Mine still freezes ever since jaunty. I have i865 chipset. I still have to use the older Intel-2.4.1 driver.

---

### Post by zevans on 2009-10-03
> **VMC said:**
> What Intel chipset do you have. Mine still freezes ever since jaunty. I have i865 chipset. I still have to use the older Intel-2.4.1 driver.

Freeze bugs that Jaunty had on release should all be fixed with recent updates (to Jaunty I mean) - do you have an updates repository enabled?

Anyway - my Karmic upgrade finally worked and so far only problem I have had is a modinfo crash which doesn't actually seem to have done any harm anyway...

---

### Post by Mr. Picklesworth on 2009-10-03
> **unimatrix said:**
> Sooo.. could someone make a PPA for X server 1.7?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
Doesn't have 1.7 yet, but that's the idea. (And it's a pretty well supported PPA, from what I understand - although I have not used it yet).

> **6205 said:**
> who cares for 1.7? you will not notice difference.. same for newer kernel..

This release has [XInput 2]("http://who-t.blogspot.com/2009/10/xi2-and-mpx-released.html"), which is built out of concentrated awesome and pretty well makes XOrg the best thing out there, in my books. In short: after 20 odd years, the one pointer per display thing is now dead. Add some good client software support down the line (which should occur pretty smoothly) and the competition will be jealous.

---

### Post by VMC on 2009-10-03
> **zevans said:**
> Freeze bugs that Jaunty had on release should all be fixed with recent updates (to Jaunty I mean) - do you have an updates repository enabled?

Anyway - my Karmic upgrade finally worked and so far only problem I have had is a modinfo crash which doesn't actually seem to have done any harm anyway...

I keep jaunty current with updates, if that's what you mean. I use aptitude. Do you still have to use nomodeset on jaunty?

---

### Post by zevans on 2009-10-07
> **VMC said:**
> I keep jaunty current with updates, if that's what you mean. I use aptitude. Do you still have to use nomodeset on jaunty?

Yeah, I meant -updates, nothing exotic, but then I remembered modesetting depends more on the kernel than the gfx driver, if anything, but you need a minimum level of both. I have lost track of what got fixed or not in Jaunty's kernel, sorry. :-)

Anyway - if you install xorg-edgers and 2.6.31 everything will fly and you'll wonder why you didn't do it a month ago, trust me! Why not try the kernel first.

---

### Post by zevans on 2009-10-07
BTW does 1.7 (or will 1.8) include panning, and if not who the heck decided multi-pointers was more important?

---

### Post by Mr. Picklesworth on 2009-10-07
> **zevans said:**
> BTW does 1.7 (or will 1.8) include panning, and if not who the heck decided multi-pointers was more important?

The guy who built [multi-pointer support]("http://wearables.unisa.edu.au/mpx/") in his own branch, on his own time, because he saw the power of it and doesn't do anything with that other part of X?

---

### Post by markbuntu on 2009-10-07
multi-gpu support is back, yay!
Now maybe compiz will work with xinerama.

---

### Post by zevans on 2009-10-08
> **Mr. Picklesworth said:**
> The guy who built [multi-pointer support]("http://wearables.unisa.edu.au/mpx/") in his own branch, on his own time, because he saw the power of it and doesn't do anything with that other part of X?
Fair enough then, hats off to him!

---

