---
title: "System wildy unstable after Breezy-Dapper upgrade."
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2006-11-14
I am not an expert on Ubuntu or Linux in general--in fact, I know little of each, which is why I tried Ubuntu to begin with.

We had a satisfactorily operating Breezy setup, completely up to date.  I opened the update manager, which (as it had long been doing) offered me the option of a one-click upgrade to Dapper.  I clicked the button, read the unhelpful blah-blah, and told it to proceed.  It seemed to download everything correctly (after a couple of hours), then went into actual install.  Then the fun:

It began asking about obscure (to me, anyway) configuration files that, it said, had been customized or modified (few or none by me, so apparently by some script or other).  As a novice, it was impossible for me to make any rational decision whether I wanted to keep the old, customized version or accept the new one; I may even have split the decisions (had I known what I was getting into, I'd have kept careful records, but I had had the impression that this was a fully automat process).

There was also a stop or near-crash at one point over something with the word "alarm" in the title (yes, I should have recorded it more carefully, but I didn't in being so worried about recovering somehow).  It did in some way, after some box-clicking, pick up and finish.

At the end, the system re-booted and seemed to come up ok.  The PCMCIA line on the roll-up shows "failed", but it's a desktop PC, so I wasn't worried.

The system is now essentially unusable.  It looks just fine, and one can do a few things, but at some early point in trying almost anything, the system either locks totally (the CPU activity applet stops dead) or goes to a totally black screen.

Example: start Firefox; home page, a local HTML file, appears ok; click on, say, Yahoo front page; loading marker starts, then freeze.

Another: start Synaptic; click on "Mark Updates"; freeze.

Another: open file manager; move to /etc/X11; click on config file; freeze.

(Needless to say, I am posting this message from a different system.)

I have no idea where to even start.  Help, please??

-- 
Eric Walker

---

### Post by Dr. Nick on 2006-11-15
fiirst thing I would try is to boot into the old kernel, At the start up screen pick the previous kernel and see if the freezes stop
 
The activity you describe seems totally random and unlinked to a single application, so I would look at system wide things like the kernel to be the first possibility.

---

### Post by owlcroft on 2006-11-15
> fiirst thing I would try is to boot into the old kernel, At the start up screen pick the previous kernel and see if the freezes stop

Yes, thank you, that eventually occurred to me and I tried it, and we do get a more or less functional system.  There are some oddities not worth individually noting here, but--possibly from ignorance of how this all works--I am attributing them to a mild mismatch between the kernel and the (presumably) updated rest of everything.

>The activity you describe seems totally random and unlinked to a single application, so I would look at system wide things like the kernel to be the first possibility.

I agree that it would have to be some system-wide (or nearly so) thing.  That reverting to an older kernel helped is, of course, indicative.  I still feel the most likely cause is that I either kept some old config file when I should have accepted the newer one, or the reverse, i let a new file over-write some customized thing.  About the only thing I recall ever fiddling with was the xconfig file, with which I followed some obscure instructions to get it to point at the correct driver; I am wondering if that is the issue, if the thing is freezing when it tries to do some particular form of screen re-paint or some such.

My biggest problem is simply "What now?"  I have a presumably updated system running under an older kernel, not something I would want to keep going with forever.

Any further thoughts, anyone?

(And, if any developer happens to read this, how about some more helpful guides and processes when it comes to config files, such as making available as an applet some sort of "reversion tick box" where one can try switching between old/new, individually or in combination, all config files that had been customized but were--or were not--over-written?  Is that so hard?  If Ubuntu is to be the success everyone wants, it *has to* be easily usable even by folk who are not only not Ubuntu geeks or Linux geeks, but computer geeks at all--a "one-click" update had best be a one-click update, not a one-click-then-several-incomprehensible-technical-decisions update.)

---

