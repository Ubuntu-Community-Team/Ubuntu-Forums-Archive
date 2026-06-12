---
title: "installing ubuntu over debian"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by mauijohn on 2005-09-22
I have debian installed.

What do I need to do to install ubuntu and get rid of the debian?

I've burned an install Cd.

---

### Post by az on 2005-09-22
Well, if you are running a current debian box (sarge or sid) you can always dist-upgrade to the preview release of Breezy.  It will become stable in less than a month.

Otherwise, if you want to run the latest stable version of Ubuntu (hoary), you can just reinstall by running the ubuntu installer and selecting your current debain partition as the target partition.

If you are running a reasonably old (like six months since you upgraded libc6) debian box, you can dist-upgrade right to Hoary.

---

### Post by bsussman on 2005-09-22
If you're going to abandon everything, including personal files, just install ubuntu, reformatting your partition(s).

if you have things you want to preserve, consider moving them out of the way and also consider making a /home partition so that future major changes and upgrades are easier.

using a separate /home, I brought along a lot of my mepis config and user stuff when I moved to ubuntu - in fact I still have a mepis partition (needs reclaiming :)) BUT

Don't expect all your debian config stuff to work unchanged.  ubuntu can be a little different.

---

### Post by mauijohn on 2005-09-22
I got to the "starting partitioner" and now I just have blue screen

---

### Post by mauijohn on 2005-09-22
I'm using 5.10

---

### Post by az on 2005-09-22
CTRL-ALT-F3 and look at the error, then lok to see if the bug has already been filed....

---

### Post by mauijohn on 2005-09-22
No matching physical volumes found

No volume groups found

---

### Post by az on 2005-09-22
Colony 4 , preview or a daily release?

---

### Post by mauijohn on 2005-09-22
Preview, I think

download from the ubuntu site

---

### Post by mauijohn on 2005-09-23
Downloaded 5.04 and got a good install except the mouse is not active.
Something to do tomorrow

---

### Post by rplantz on 2005-09-23
mauijohn,

Why are you changing to Ubuntu?

I've been using Ubuntu for several months now and am thinking of installing Debian. I should mention that I have an AMD64 and am running in 64-bit mode. Several things don't work.

I'm thinking that Debian will give me more flexibility. Am I wrong?

If you have a few moments, I'd like to hear your reasons for switching.

Oh, I'm retired. So I have time to play around with things. (It's great!)

Thanks,
Bob

---

### Post by bsussman on 2005-09-23
[QUOTE=rplantz]mauijohn,

I'm thinking that Debian will give me more flexibility. Am I wrong?

[/QUOTE]

I think you are...:-P

In fact, I do not believe it can give you more flexibility since ubuntu is a Debian distribution.

I remember when there was absolutely no package tools except make. It was hard to decide what software to install, both in terms of function and dependencies. Of course there were only a couple of thousand packages back then.

Now there are 8, 9, 10 thousand (?)

ubuntu installs a subset of the total megaverse of available packages, tuned to work together, kept uptodate slightly more conservatively than the Debian gigantaverse.

You can install any package that you want, building the ones that need it, from the Debian plextoverse.

What you have gained by starting with ubuntu is a sane subset that you didn't need to define.

If your purpose is to understand how to design a distribution, install debian. The experience will probably qualify you, technically, to design the replacement for mepis, ubuntu, DSL, TIny etc, etc, etc

If your purpose is to have a larger software base than vanilla ubuntu, make sure you have added uni and multi-verse, and start installing things.

---

