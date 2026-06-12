---
title: "App intergration into Live Usb"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by shannon-e-webb on 2014-09-18
Hi :-)
Sorry if this isn't posted in the right category.
I was wondering if someone might be able to point me in the right direction, I'm trying to figure out how to go about customizing a few packages incorporated in the lubuntu 14.04 32bit Live usb image - I'd like to end up with a modified iso that can be deployed like a normal one for some diagnostics/auditing work.
i've had a bit of a search and can't really find a definitive guide that has Lubuntu in mind - I did find a good ubuntu one some time ago but I can't find it again and figure the lubuntu process is much the same.

from my understanding i have to do something along the lines of incorporate the packages into the local repository and update the apt database within the liveusb image.
and I can see 2 ways that I might be able to do this (but im not sure)
[LIST=1]
[*]offline, using a few tools in terminal - the ubuntu guide I spoke of used this method and it was quite long and involved.
[*]online, making the changes while running the release (as a live or installed os idk) then cloning and/or converting that back into a live image. I remember coming across a tool once in some distro I played with that could make a live image out of the one running.
[/LIST]

Ultimately I'd really to make it a customized clean live os only image (no installer prefered) with little or no user persistence and maintaining flexible h/w compatibility (if not also incorporating a few 3rd party drivers into the repository aswell). I'm aware there are a number of other disto's (kali, caine, etc) dedicated to this function but they don't really suit my needs (and lubuntu is so light and neat :P).

I happy to do the bulk of the legwork, any input would be most appreciated.

Cheers Shannon,

---

### Post by grahammechanical on 2014-09-18
Why not just create a Lubuntu Live USB stick with persistence and then remove unnecessary applications and add any diagnostic and repair utilities as you choose. What do you really want? A  diagnostic/repair remix ISO image? Or a diagnostic/repair USB live session?

Other have gone ahead of you.

[http://www.gfi.com/blog/top-5-free-rescue-discs-for-your-sys-admin-toolkit/](http://www.gfi.com/blog/top-5-free-rescue-discs-for-your-sys-admin-toolkit/)

[http://sourceforge.net/projects/systemrescuecd/](http://sourceforge.net/projects/systemrescuecd/)

Regards.

---

