---
title: "Ubuntu 10.10 with Grub 2?"
date: 2010-02-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by longtom on 2010-02-19
Hi,

wasn't quite sure where to place this question - so if it needs moving please move, mods.

I just want to know if Ubuntu 10.10 will ship with Grub 2 or will it, for the sake of stability, resort to Grub Legacy?

---

### Post by matthew on 2010-02-19
This is an appropriate location for the question.

9.10 already shipped with Grub2 and that is the expected and intended direction for the future. More here: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Elfy on 2010-02-19
I thought that lucid was so I moved it ... we can move it back if necessary :)

---

### Post by matthew on 2010-02-19
> **forestpiskie said:**
> I thought that lucid was so I moved it ... we can move it back if necessary :)

Either place is fine.

---

### Post by Slug71 on 2010-02-19
> **longtom said:**
> Hi,

wasn't quite sure where to place this question - so if it needs moving please move, mods.

I just want to know if Ubuntu 10.10 will ship with Grub 2 or will it, for the sake of stability, resort to Grub Legacy?

Ubuntu has had Grub 2 since Karmic Koala 9.10.

---

### Post by Merk42 on 2010-02-19
What lack of stability are you implying regarding Grub 2?

Also, **Grub legacy is no longer maintained** which is why Karmic was switched to Grub 2 in the first place.

---

### Post by longtom on 2010-02-19
> **Merk42 said:**
> What lack of stability are you implying regarding Grub 2?

Also, **Grub legacy is no longer maintained** which is why Karmic was switched to Grub 2 in the first place.

Thank you for all your answers.

I don't care too much what is maintained, I care about what works.  Grub 2 works for some, I know.  I doesn't so for me and for many others, so I was wondering.

There are other distributions who think different so even with their newest releases.  I'll give either a spin and decide afterwards.

---

### Post by Merk42 on 2010-02-19
> **longtom said:**
> Thank you for all your answers.

I don't care too much what is maintained, I care about what works.  Grub 2 works for some, I know.  I doesn't so for me and for many others, so I was wondering.

There are other distributions who think different so even with their newest releases.  I'll give either a spin and decide afterwards.

But what specifically doesn't work about it?
Since Grub2 is maintained, you could file a bug so that way Grub2 would, at least in your case, work just as well as Legacy.

---

### Post by dino99 on 2010-02-19
hi guys,

have had some troubles when i've upgraded grub1 to grub2. The reason was grub1+grub2, so if we install grub2, and you might, grub-legacy have to be removed/purged from the system and let grub2 alone.

the trouble was due to os-prober still finding settings into menu.lst (grub1) and never report good settings from grub2.

10.10 ? wait man, right now we wait to 10.04 first, then we will see :P

---

### Post by longtom on 2010-02-20
> **dino99 said:**
> hi guys,
10.10 ? wait man, right now we wait to 10.04 first, then we will see :P

You're absolutely right - my mistake.  I meant to write 10.04.  Since it is a LTS I was thinking a stable Grub would make sense.  Alas, I appear to be wrong.  
I am not in the mood to loose my dual boot again and I am sure so are some other users, so I will certainly be extra careful.
I am still using 8.04 (again) on my mission critical machine.  I like stuff which works reliable on that machine.  
I am more than willing to run and test beta and even alpha software on a different machine, however, I don't like it to be part of a potentially stable and long term supported system.
I don't know if this makes sense to some of you. I know, there are some Ubuntu fundamentalists around here to which this sounds like heresy and I fully expect this thread to be closed in a while as others have been.  

As I said, I give all a spin and see what suites me best. 

Thanks for reading.

---

### Post by autocrosser on 2010-02-20
There have been long & sometimes heated debates in the testing forum about Grub vs Grub2---I was a early-adopter of Grub2 & like the direction it is heading.

Sure, it is not as stable in some cases as Grub---but according to the Grub developers Legacy Grub could not be patched much more & a new design was needed/required. I respect their plan & see that it will be as good or better when it reaches the 2.0 release--it's close, but not yet.

That being said, it easily meets all my needs & I have a 5 OS booting system--4 linux installs & (cough) Windows XP for work reasons....You might re-look the current Grub2--it's really getting there.

As for "some Ubuntu fundamentalists around here to which this sounds like heresy  and I fully expect this thread to be closed in a while as others have  been" ---I do not think you are giving the people in this forum a fair go....I stay in this forum BECAUSE the group here is MORE open-minded---not less.

---

### Post by ranch hand on 2010-02-20
kansasnoob, a regular on this forum, has an excellent How To for reverting to grub-legacy from grub.

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I do not reverting is a good idea as there are too many great ways to make grub do the job.  However, there may well be certain combos of hardware that just do not work well with grub.

In that case please use that How To when reverting.  There are a couple of pitfalls that may get you other wise.

It is important to remember that grub-legacy is no longer supported.

---

### Post by matthew on 2010-02-20
> **longtom said:**
> Since it is a LTS I was thinking a stable Grub would make sense.This is a common misperception. LTS means that the release will be supported longer, not that it is promised to be any more or less stable. The decision on which version of specific pieces of software to include is based most often on which version will be most easy to support (especially with security updates) over the lifespan of the release.

> **ranch hand said:**
> It is important to remember that grub-legacy is no longer supported.
And this is the crux of why Grub2 is being used, as mentioned previously, beginning in 9.10. If software is no longer supported, that also means no security updates...

---

### Post by nanog on 2010-02-20
> I am more than willing to run and test beta and even alpha software on a different machine, however, I don't like it to be part of a potentially stable and long term supported system.


Then you should be concerned about your use of grub legacy on 8.04 because not only is it a **beta** according to grub developers but it is now deprecated (as in not supported, not developed, not maintained, obsolete, dead etc.)

Your post smacks of concern trolling because:

1) Grub2 is not installed during upgrades. 

2) You do not list a single problem you have experienced with Grub2.

---

### Post by emarkay on 2010-02-20
Be specific on the issue - what about GRUB2 is not working on your system.  
Did you upgrade or do a new install?
Have you tried Karmic or Lucid in your system to confirm yhe GRUB2 issue is still there?
To me it's a natural progression, one can't get 8-track players in a new car these days; progress progresses.

---

